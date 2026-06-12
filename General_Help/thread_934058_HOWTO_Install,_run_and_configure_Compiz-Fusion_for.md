---
title: "HOWTO: Install, run and configure Compiz-Fusion for Hardy Heron 8.04 LTS."
date: 2008-09-30
forum: General Help
---

### Post by arkticcool on 2008-09-30
[COLOR="Red"]This HOWTO does not come with any guarantee, use at your own risk.[/COLOR]

**Prereq's (Hardware/Graphics/Drivers): depends on graphics card; (NVidia for me);**

[http://wiki.compiz-fusion.org/Hardware/ATI](http://wiki.compiz-fusion.org/Hardware/ATI)
[http://wiki.compiz-fusion.org/Hardware/Intel](http://wiki.compiz-fusion.org/Hardware/Intel)
[http://wiki.compiz-fusion.org/Hardware/NVIDIA](http://wiki.compiz-fusion.org/Hardware/NVIDIA)

Make sure you have installed the latest driver. Even though compiz is well supported, there still is a black list of problem causing configurations which can be found here: [http://wiki.compiz-fusion.org/Hardware/Blacklist](http://wiki.compiz-fusion.org/Hardware/Blacklist)

**Installation:**

Go to Add/Remove programs **(Applications > Add/Remove)**
Type in: advanced into the search box.
Check the box next to Advanced Desktop Effects Settings (ccsm).
Apply changes, install and run. **(System > Preferences > Advanced Desktop Effects Settings)**

**Configuration:**

Tick the effects in the following images, too long to type up. Easier for you to copy.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=86817&stc=1&d=1222766631[/IMG]
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=86818&stc=1&d=1222766631[/IMG]
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=86819&stc=1&d=1222766631[/IMG]
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=86820&stc=1&d=1222766631[/IMG]
[B]
Configuration Detailed: (Individual settings on the various animations.):[/B]

Desktop Cube: Click on Desktop cube, and open Apperence > skydome section.
Select a good image as your skydome (must be hi-res e.g. 10mb+), examples can be found here; [http://compiz-themes.org/index.php?xcontentmode=6110&PHPSESSID=f2ceb95cc83591925a15abe53a709dfd]("http://compiz-themes.org/index.php?xcontentmode=6110&PHPSESSID=f2ceb95cc83591925a15abe53a709dfd")
(I used Nebulae, thx to Mat).
Create a folder in your default Picture folder. **(Places > Pictures > Right-click create folder "compiz_fusion")**
Save the image you have chosen there.
Go back to the CompizConfig Settings Manager and insert the skydome image. Tick the boxes marked Skydome and Animate Skydome. Set the gradient to whatever you like, however if you don't want it to affect your image, click on the colours and change opacity to 0 (for both).

No go to the Behaviour tab next to the Apperance one.
Double all the values for acceleration, speed and timestep. Creates a more smooth rotation.
Lastly go to the Transparent Cube tab and make the cube have a 75% opacity on cube rotation.

Go back to the main area, and click on the 3D Windows plugin. Change the animation speed to 1. Then go to the Window depth tab and make the window colours (in/active) transparent by clicking on them and setting opacity to 0.

Now go back and enter the Animation plugin. Change all the effects in the white boxes to Random. Click edit and choose random for each of the values.

Go back to Cube reflection in the main area, and change the Ground colours to transparent. Then change both the Reflection ground size and intensity to 1.

Go back to Reflection in the main area, and tick the box that states Reflection for windows.

Finally we have to do the Cube caps, which are the bottom and top of the cube. Go to Cube caps at the bottom of the main area. Change Cube color (both top and bottom) to transparent. Save two cube cap images to your compiz folder from before and insert by clicking edit on the default values and selecting the files you want to have. Examples of cube caps can be found here; [http://compiz-themes.org/index.php?xcontentmode=6120]("http://compiz-themes.org/index.php?xcontentmode=6120")
Then go to the behavior tab, and tick all the boxes.

Exit and wallah you are done.

Here is a link to common keyboard shortcuts to make you a pro Compiz-Fusion user; [http://wiki.compiz-fusion.org/CommonKeyboardShortcuts]("http://wiki.compiz-fusion.org/CommonKeyboardShortcuts")

---

