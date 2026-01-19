# Launch Controller

Custom project-icarus launch controller

# Use Cases (WiP)

The following use cases should instruct the design

## Launch Director
* provision boxes and controllers
* charge boxes and controllers
* shut down and store boxes and controllers
* decomission boxes and controllers

### Privision Boxes and Controllers
1. Turn off controller and boxes
2. open controller and boxes and set provision jumpers
3. close and power up controller
4. connect to the wifi network projects (ssid: ??)
5. connect to the embedded web interface
6. in the web page, set
  * club name
  * radio channel
7. power up each box one by one
  1. see the new box appear
  2. name the box
  3. hit the provision button
  4. see it blink once to indicate it is being provisioned
  5. it will chirp when it is done (indicating radio link)
8. power down controller and boxes
9. open controller
10. remove jumpers from controllers are boxes
11. close boxes and controllers


## Launch Control Officer
* start up and shut down the range
* quickly and easily see status of boxes and controller
* see continuity status and arming status of boxes
* select and clearly identify which box is selected
* launch selected pad
* launch two selected pads for drage racing
* mark pad for recycle

## Flyer
* quickly and easily see if box is armed or safed
* quickly and easily see which channels have continuity

# Requirements (WiP)

* controller and box display/indicators easily readable in direct sunlight with polarizing sunglasses
* controller and box display/indicators easily readable at night
* clear indication of arming/safe status with both sight and sound
* tactile switching of arming/safe
* presense detection to inhibit launching when people detected
* power on self test to ensure system is in safe operating condition
* authenticated and encrypted communications
* unsafe conditions cannot be made by disruption of comms
* easy and intuitive paring and transitions
* 8?A continuous firing current
* short circuit protection on pyro channels
* battery lasts all day and is replacable/swappable
* solar charging is supported
* arming/selection indicator on box can be seen and heard from LCO table
* firing indicator can be seen from LCO table and heard from LCO table
* indicator can be raised to improve visibilty
* boxes and controller are dust and water proof
* all switches are tactile
* accidentally powering off a box/controller is easily recoverable

# References to Other Works

* Altus Telelaunch https://altusmetrum.org/TeleLaunch/
  * Schematics - https://altusmetrum.org/TeleLaunch/telefireeight-v2/telefireeight-sch.pdf
  * Manual - https://altusmetrum.org/AltOS/doc/telelaunch.html

# Messages

message format
u8 id
u8 msg type
u8[] msg

ack message
u8[8] iv

gps message
u32 lat
u32 lon
u8 sats
u8 hdop

cont message
u8 chan
u8 battery

armsafe message
u8 status - 0 safe, 1 armed, 2 inhibited
u8 battery

box selected message
bool selected

launch message
u8 channel (bitmask)

launch rejected
u8 error (0 - inhibited, 1 - low battery, 2 - box is not armed)
