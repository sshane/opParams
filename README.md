# op_params

This repo is just a backup of op_params. To install into your own fork, just grab the files in the [`openpilot`](/openpilot) folder and place them into your repository in their respective directories.

1. Make sure you add your new parameter to [`op_params.py`](/openpilot/common/op_params.py) filling out the `default', 'allowed_types', and 'live' keys.
   * You can also change the read, or update frequency in that file.
2. In the file you want to receive updates, use this code in place of the variable you want to use.
   * So for camera offset, we can do this in `lane_planner.py`:
   ```python
   from common.op_params import opParams
   op_params = opParams()
   CAMERA_OFFSET = op_params.get('camera_offset', default=0.06)
   # CAMERA_OFFSET = 0.06  # m from center car to camera
   ```
   * The default will be used if the user doesn't have the parameter.

3. Now to change live parameters over ssh, you can connect to your EON with your WiFi hotspot, then change directory to `/data/openpilot` and run 'python op_tune.py'.
   * Here's a gif of the tuner:
   <img src="gifs/op_tune.gif?raw=true" width="600">