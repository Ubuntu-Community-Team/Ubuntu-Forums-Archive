---
title: "external USB Drive not mounting automatically"
date: 2008-07-13
forum: Hardware
---

### Post by Kilarin on 2008-07-13
I messed something up. :(

Background: I have a cavalry 500gig external usb hard drive formatted ntsf-3g.  Ubuntu mounts it just fine on startup usually.  or it used to anyway.  :(

Recently I noticed that whenever I attempt to delete a file on this drive I get the error "can not move file to trash, do you want to delete immediately?"  I think this started right after I upgraded to 8.04.

Looking on the forums here, I saw a suggested fix for the problem that was to set a mount option of "user" on the drive.  So, thinking I knew what I was doing, I rightclicked the drive on my desktop, went to properties/drive/settings and added USER to the "Mount Options" field.

The result was that the usb drive wouldn't mount at all.  YIKES!

So, in an attempt to fix this, I did sudo gconf-editor
I went to the folder system/storage and was able to correct the issue there by finding the drive entry and deleting the "user" parm.

Well, sort of correct the issue.  Now the external usb drive will mount just fine, but ONLY if I turn it off and back on after the computer has booted.  flick the power switch, ubuntu finds the drive and mounts it with no problem. BUT, it will not mount automatically on startup the way it used to.  On boot its like ubuntu thinks the drive isn't plugged in.  Flip the power and it mounts again just fine.  There is NOTHING wrong with the drive itself because it will still mount automatically on boot when I boot windows.

Obviously I've goofed something up with how this drive is mounted.

So, any advice on what I messed up and how to correct it so that my external usb hard drive will mount automatically on boot again would be greatly appreciated.  

Once I get THAT fixed, I can go back to trying to figure out why the trash can is broken on that drive. :)

---

