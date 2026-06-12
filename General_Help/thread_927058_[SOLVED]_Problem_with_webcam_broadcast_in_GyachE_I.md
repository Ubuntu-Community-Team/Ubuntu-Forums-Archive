---
title: "[SOLVED] Problem with webcam broadcast in GyachE Improved"
date: 2008-09-22
forum: General Help
---

### Post by bedhead75 on 2008-09-22
I've downloaded and installed the latest GyachE Improved (v.1.1.48 ) from the Synaptic Package Manager.  It seems to run fine execept when users try to connect to my webcam (Logitech Quickcam Communicate STX).  I can view other people's webcams fine.  When I start my webcam, it also works fine as I can see the video from it in a window on my screen.  It is enabled in the setup as "/dev/video0".  When I try to invite other users to see my webcam, they still can't connect and get an "unable to connect" error message on their end.  I have also made sure that my broadcast is enabled by clicking on "broadast".  Invited users just can't seem to connect and they don't show up on the users list for the people who are connected.  I don't have similar problems running Yahoo Chat from Windows XP and both webcam broadcast and receive works perfectly. Does anyone have a similar problem or a solution?

---

### Post by Ubulindy on 2008-09-24
I had this problem forever. It drove me absolutely nuts. Forums were of no help. Here, is a simple and quick work around thats so easy, you're going to want to fall over.
Go into Synaptic, or your terminal, and uninstall anything to do with "v4l"  which is "video4linux" Turns out, you dont need it, and it conflicts!  Who knew? LOL  :-P

---

### Post by spiderbatdad on 2008-09-24
> **Ubulindy said:**
> I had this problem forever. It drove me absolutely nuts. Forums were of no help. Here, is a simple and quick work around thats so easy, you're going to want to fall over.
Go into Synaptic, or your terminal, and uninstall anything to do with "v4l"  which is "video4linux" Turns out, you dont need it, and it conflicts!  Who knew? LOL  :-P

That sounds a little risky. For example libpt-1.10.10-plugins-v4l include the ubuntu-desktop metapackage, and will remove ubuntu-desktop if you try to remove the package.
I occasionally have the same problem with broadcaster and havent found a good solution. I set permissions to automatically allow friends (everytime i start the app) and have the other party request the cam rather than invite the other party to view.

---

### Post by raquel goldstein on 2008-09-29
I have a similar scenario with gyache. I can use the webcam with Ekiga just fine so i am assuming the problem is specific with gyache. Here are the specific error messages I get, can anyone guide me in what to do?

this is the error i get when i try to start my webcam using gyache:
"An error occurred at 'ioctl VIDIOCSPICT'
  could not set camera properties"

"error while querying mmap-buffers"

---

### Post by bedhead75 on 2008-10-01
Somehow everything started to work just fine after rebooting my computer and I've had no problems with webcam broadcast since.

---

