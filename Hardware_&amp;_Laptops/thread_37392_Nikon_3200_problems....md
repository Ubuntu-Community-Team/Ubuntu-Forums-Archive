---
title: "Nikon 3200 problems..."
date: 2005-05-27
forum: Hardware &amp; Laptops
---

### Post by momaw27 on 2005-05-27
Hi!

I am trying to get my Nikon 3200 camera to work, but I am running into problems...

When I connect my camera via USB and turn it on, it mounts but as Removable Media... not a camera.

Also, a Warning Box pops up asking me if I want to import the pictures from my inserted media.  Then when I say yes, gThumd opens but does not import automatically... I have to hunt through the directories to get to the pictures.

Then, when I try to go in and import my pictures manually, I get this error:

An error occurred in the io-library ('Bad parameters'): Could not find USB device (vendor 0x4b0, product 0x121). Make sure this device is connected to the computer.

Any thoughts?

Thanks!

I love Ubuntu!

Beau

---

### Post by David Haas on 2005-05-30
momaw27--I got error messages when I first tried to download photos from my Nikon Coolpix 3700, though I can't recall whether they matched the ones you got. Here is how I download now. I connect the camera to the computer with the USB cable. Then I open gThumb. Then I turn on the camera. Then I click "File" in gThumb and from the drop-down menu select "Import Photos". Now that my camera has previously been selected, thumbnails of all stored images immediately appear in another box titled "Import Photos". You will need to select your model from the list of cameras in gThumb if you haven't alreadt done so. At the bottom of this box is a bar called "Import". Click this and all your stored photos are downloaded into a new directory in Home. Well, give it a try.
David

---

### Post by maxweld on 2005-09-11
Hi - Have you guys had any luck with this. I have exactly the same problem as described by Beau - but with a Nikon Coolpix 5000. I have already tried exactly as indicated by David, but that is when I get the problem.

Thanks
David (another :-)

---

### Post by prostar on 2006-11-02
Hello,

   I have exactly the same  problem as described by the OP.  Using gThumbs it gives the "device ID" etc...  I used dmesg and can see the exact same Manufactrer and device id it is looking for.  

Any help please??!!

As a side question.  Where does a user look to find all these peices of information.  I know of dmesg(command).

My machine is an AMD 64 desktop.

---

### Post by prostar on 2006-11-02
After a little more searching I found a work around...

Set the camera to be a USB flash drive, then mount it as a folder.  

I would still like to get it working with F-Spot though....

---

