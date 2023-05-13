# Conway's Game of Life in WebGPU

The provided code is an HTML document that demonstrates a simulation of Conway's Game of Life using WebGPU. It renders the simulation on a canvas element and updates the state of the cells at regular intervals. Check it out at https://qayyumayaan.github.io/webgpu/. 

I wanted to learn how to use WebGPU, so I followed the guide at https://codelabs.developers.google.com/your-first-webgpu-app. 

The code begins by defining several constants, including the grid size, update interval, and workgroup size. These constants are used throughout the code to configure various aspects of the simulation.

After that, the code retrieves the canvas element using the `querySelector` method and checks if WebGPU is supported in the current browser. If WebGPU is not supported, an error is thrown. Otherwise, the code proceeds to request a GPU adapter and device for rendering with WebGPU.

Next, the code configures the canvas for WebGPU rendering by obtaining the preferred canvas format and using it to set up the context.

The code then creates a buffer containing the vertices for a single cell. These vertices define the shape of the cell in the simulation. The buffer is created with specific properties, such as label, size, and usage, and the vertex data is written to the buffer using the device's queue.

A vertex buffer layout is also defined, specifying the format and attributes of the vertices.

The code continues by creating a bind group layout and a pipeline layout. These layouts define the structure of the data passed to shaders during rendering and compute operations.

Next, a shader module is created for rendering the cells. The shader code defines the behavior of the vertex and fragment shaders, including the transformation of cell positions and the calculation of cell colors.

Using the shader module, a render pipeline is created to render the cells. The pipeline is configured with the shader module, vertex buffer layout, and render target format.

Following that, a compute shader module is created to update the state of the cells based on the rules of Conway's Game of Life. The shader code defines a function that determines the active state of each cell based on its neighboring cells.

A compute pipeline is then created using the shader module. This pipeline will be used to update the cell state during the simulation.

The code proceeds to create a uniform buffer that describes the grid size. This buffer holds the grid size as uniform data that can be accessed by shaders.

Two storage buffers are also created to hold the current and next states of the cells. These buffers are used to read and write the cell state during the simulation.

The code initializes the cell state array with random values and writes the array data to one of the storage buffers using the device's queue.

Two bind groups are created, each containing references to the uniform buffer and the storage buffers. These bind groups are used to pass data to the shaders during rendering and compute operations.

A function named `updateGrid` is defined, which performs the main steps of the simulation. It creates a command encoder, begins a compute pass, dispatches compute workgroups to update the cell state, and ends the compute pass.

Then, it begins a render pass, clears the canvas, sets the render pipeline, bind group, and vertex buffer, and draws the grid using the cell pipeline. Finally, it ends the render pass and submits the command buffer to the device's queue.

The `updateGrid` function is scheduled to run at regular intervals defined by the `UPDATE_INTERVAL` constant using the `setInterval` method.

In summary, this code sets up a WebGPU environment, defines shaders for rendering and updating cells in Conway's Game of Life, and performs the simulation by updating the cell state and rendering the grid on a canvas.
