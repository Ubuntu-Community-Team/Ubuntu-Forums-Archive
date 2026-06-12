---
title: "camera mounts twice?"
date: 2013-04-30
forum: Hardware
---

### Post by Buntu Bunny on 2013-04-30
I currently have a Kodak Easyshare digital M583 camera. After I got it, I discovered it causes all kinds of grief for Linux users, including all flavors 'buntu. Still, I got it to import the photos to my computer after I disabled the share option. The only problem has been that it imports them twice, once as blank dummy images, the other as the actual photographic images. I then have to go through my photo folders and manually delete the dummies. 

When I first plug the camera into my computer, I get two simultaneous message boxes. One says the camera is detected, the other that it is unable to mount the camera

> Error initializing camera: -60: could not lock the device

I click ok and Shotwell opens. When I attempt to import, I get a message box telling me Shotwell needs to unmount the camera to access it. I click "unmount" and it shows me the preview of the images on the camera. If I try to import these, I get a "failed to import due to camera error" message. I then select the camera from Shotwell's camera listings in the sidepane, and the images  import, no problem, except for the blanks from the failed first attempt. 

I noticed today, that if I have file manager open, the camera is listed twice under devices. One is at at gphoto2://[usb:002,002]/store_00010001. It contains 2 folders, DCIM and MISC. The other is at gphoto2://[usb:002,002]/store_00020001. It contains two files, IREVIEW.DB and ISHARE.DB.

I'm not sure if the camera is indeed mounting twice, but I am wondering if there is any way I can change it's behavior. It would be nice to not have to go through the extra steps, as well as having to deal with those blank dummy images. I've been willing to live with it because this is the only camera I have at the moment, and for $100, it does take good quality photos.

---

### Post by eric-yorba on 2013-04-30
I know some Kodak cameras out there have more than one mounting "mode."  This is typically set through the camera's on-screen menu.  If your camera has that, you might try switching modes and see if that helps.

The other thing you might consider is just using an SD card reader and bypassing the camera.

---

### Post by Buntu Bunny on 2013-04-30
Eric-Yorba, thank you for responding. I tried both of your suggestions. 

The camera's own on-screen menus offered a computer connection option, either Kodak or "other." The only modes I could find were screen modes. So there wasn't much I could do with that.

Next I tried a card reader. This was interesting. If I tried to fetch them with shotwell, I had the choice to either copy the image or import it. If I copied, it did so with no blank duplicate. If I clicked on import, I had to go through the same rigmarole I do when I plug in the camera. I also found I could simply drag the images from the SD card folder to my picture folder. 

I'm thinking that may be the easiest thing to do in the long run. It means messing with the SD card (which is a micro), but it beats going through the extra steps with shotwell. I'm grateful for the workaround, thank you!

---

