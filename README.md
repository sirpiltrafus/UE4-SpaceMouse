## SpaceMouse camera controller for UE4 editor viewports

**Compatible with UE 4.24 (4.25 untested) and probably below**  
**Compiled for UE 4.21 .. 4.25.**
# [DOWNLOAD](https://github.com/microdee/UE4-SpaceMouse/releases/latest)

Demo video: https://youtu.be/Qibig0gQWvE

You can control any 3D editor viewport currently in focus (user clicked on it). Controls are 6DOF flying camera movement type, no orbit type yet. See the picture for the default transition and rotation axis (although you can change it in Editor Preferences):

![Alt text](/ReadmeMedia/coordinates.jpg?raw=true "Coordinates")

Transition speed is controllable via the camera speed setting and the camera speed scalar of the viewport. Camera speed can be increased or decreased with configurable buttons on the spacemice. Multiple devices are supported however their data is merged together into a global context.

On default speeds (speed setting = 4) transition velocity is 1000 units/sec by default and rotation speed is 270°/sec by default. Rotation speed is not affected by camera speed settings. You can change these in the **Editor Preference** under SpaceMouse section.

![Alt text](/ReadmeMedia/settings.png?raw=true "Coordinates")

**Axis mappings** are conversions between the space of spacemice and the space of UE4. You can invert rotations and translations here by flipping the sign. The default values are my subjective preferences (as you can see in the coordinate system image above).

**Rotation/Translation Curve** are defining the 0..1 curvature from resting state to fully pushed/pulled state of the SpaceMouse puck. Dead-zone, clamping, exponent or other less useful transformations can be expressed with this. Default is 0..1 linear curve, which means no effect.

**Display Debug Information** prints HID data onto the viewport. You don't need to change **Max Hid Read Operations Per Frame**. Just ignore it.

With **Button mappings** one can remap some functionalities to SpaceMouse buttons. currently they are Increase, Decrease and Reset camera speed. Activate the toggle button next to the property to learn the desired button mapping for said function.

This plugin works with the HID device directly so no 3DxWare service is needed to run (similar how Blender does it). And I highly recommend to disable said service because it's a big pile of steaming hot garbage imo. It doesn't need you to install any drivers at all in theory. However it shouldn't interfere with a running 3DxWare service in case you need it for other less fortunate programs.

[Discussion at UE4 forum](https://forums.unrealengine.com/unreal-engine/feedback-for-epic/437-support-for-space-navigator-3d-mouse?p=1609440#post1609440)

## Known issues:

* ~~"Focus selected" is broken while this plugin is loaded~~
  * FIXED
* ~~"Piloting" is not working with the SpaceMouse~~
  * FIXED
* ~~Upon exiting the editor the engine crashes. I know why it does that but I didn't figure it out quite yet how to prevent it.~~
  * FIXED

## Known nuances
* Only free-fly mode is supported and every orbitting perspective viewport in focus is forced to be free-fly while any spacemice operates on them.
* Camera roll is not reset when one tries to navigate viewport with traditional methods
  * Maya style Alt + Right-drag dollying resets camera roll

## Would be nice to have:

* ~~Add ability to remap buttons to different actions, so one can potentially use all the buttons on their SpaceMouse Pro~~
  * ~~Implemented in Editor config, however it would be still nice to have a "learn button ID" button~~
    * SpaceMouse plugin can now learn buttons by just pushing them
* Add feature to lock camera roll.
* Add Orbit mode (probably ain't gonna happen soon)

## Credits:

* [HIDAPI](https://github.com/libusb/hidapi)
* From UE4 forums:
  * **enzo_molinari** for the plugin icon
  * **adlord** for testing with wireless devices