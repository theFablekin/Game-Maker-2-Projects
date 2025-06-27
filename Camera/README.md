Scripts for a dynamic camera created for a 2D platformer
The camera object is always at the centre of the screen,
  but the camera coordinates originate from the top left corner,
  so every frame, the object moves the camera to its own position,
  deducting half the screen width from the X coordinate,
  and half the screen height from the Y coordinate.

The object uses two state switches, embedding one into the other.
There are three 'priority' states.
  The scripted state - this is the default state of the camera, where the movement is determined by the current subscript
  The freemove state - this mode exists for debug purposes. When this mode is enabled, the user may move the camera freely with the movement keys
                        (player object movement is disabled in this mode)
  The deathcam state - In this state, the camera follows the player object. The purpose is to create a cinematic game over event, and is accompanied by other effects
The reason these three states are placed in a separate, 'higher tier' state switch from the rest,
  is because this allows us to switch back and forth between these states and the scripted states,
  without losing the current scripted state.
Essentially, we don't have to save the last scipted state to be able to toggle freemove off, for example.

There are five scripted states.
  Static state - The camera moves to a target position, and stays there.
                  The coordinates of the desired position have to be passed into the script as arguments 0 and 1.
  Follow state - The camera gently follows the player object.
                  The speed of the camera is proportional to it's distance from the target object.
  Horizontal follow - The camera follows the player object horizontally, but the Y coordinate is locked.
  Vertical follow - The camera follows the player object horizontally, but the X coordinate is locked.
  Precise follow - The camera position is instantly updated to the position of the target object or instance.
                    Meaning the speed of the camera always matches the movement of the target object.
                    This script is also used for the deathcam state.  
