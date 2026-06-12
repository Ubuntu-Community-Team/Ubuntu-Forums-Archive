---
title: "Hauppauge WinTV-HVR 1600 and Nvidia GeForce 8500 GT"
date: 2010-08-04
forum: Hardware
---

### Post by aaron_bengo on 2010-08-04
I am having trouble getting the two cards listed in the title (Hauppauge WinTV-HVR 1600 tv capture card and Nvidia GeForce 8500 GT video card) to work together. I had a fresh install of ubuntu 10.04 on my machine and everything worked flawless without the capture card in it. The x server recognized my screen (a panasonic 32" tv with VGA input) properly and allowed me to adjust all settings accordingly. I installed the MythTV Backend Master package and did a full restart. All still working perfectly. I shut down the machine and plugged the capture card into the PCI 1 slot and rebooted and the error "Ubuntu is running in low graphics mode" came up with a list of errors underneath it. I told it to restore my backed up settings and restarted again. When it loaded the screen didn't look like it should so i tried to change the resolution through nvidia XServer. It wouldn't allow me to change the res any higher than 640X480. So i shut down and pulled out the capture card and booted back up. It booted properly but still wont allow me to change the res any higher than 640X480. I had the same problem when i tried to set up the same machine using Mythbuntu 10.04 and couldn't get the problem resolved. Thats why i just decided to install plain Ubuntu and try again. I have the recommended drivers installed for the video card. I imagine that this is some sort of compatibility issue between the two cards but I'm not entirely sure. I'm not positive that this thread is the proper place for this question but I didn't think it fit in anywhere else. Any help with this issue would be great as I am trying to get a MythTV system up and running. And by the way i am a bit of a Linux newb so a bit of a detailed explanation would be great. thanks.

---

### Post by ardvark on 2010-11-09
I also have the same problem with a Nvidia 6800 and a Turtle Beach Video Advantage PCI card. The only thing I've seen in here so far was somebody was trying to get multiple video cards running. A suggestion was to blacklist each video module and reload seperately, whatever that entails. That's beyond me...

---

