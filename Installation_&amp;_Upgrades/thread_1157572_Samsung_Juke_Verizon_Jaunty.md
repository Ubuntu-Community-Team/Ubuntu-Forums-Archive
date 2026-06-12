---
title: "Samsung Juke Verizon Jaunty"
date: 2009-05-12
forum: Installation &amp; Upgrades
---

### Post by Orfintain on 2009-05-12
Jaunty doesn't seem to support data transfer to my verizon Samsung Juke phone.

I have a USB cable attachment and I get ..

"Error while copying "name of file.mp3"."
&
There was an error copying the file into gphoto2://[usb:002,003]/.
&
Error writing file: -108: No such file or directory"

I have tried various file names/types.

Anyone have any ideas?

---

### Post by xmunk on 2009-05-13
working for verizon i will tell you that most brew phones ie juke will not work easily.  i seem to remember somewhere in our system there is a guide that tells how to do it but if you call you will probably get told its just not supported.  you have to get to tier 2 tech support to get any help at all and they will have trouble finding it.  i take 100 or so calls a day and have been there for 1 year and have never heard linux on a call if that tells you anything

---

### Post by Orfintain on 2009-05-13
When I had 8.10 it work just fine..

Thanks xmunk, yeah the in store verizon tech support told me linux wasn't supported once..

---

### Post by Orfintain on 2009-05-17
I set it to auto open in RythumBox Music Player and now whenever I got to anything in the places menu, it opens up RythumBox instead of my documents or whichever link .. I have tried reinstalling nautalsis (sp?) does anyone know to fix this aspect?

---

### Post by Surfpup on 2009-05-18
I also have a Samsung Juke, and figured I should let you know that I managed to use Banshee Media Player to transfer music to it. I'd expect it to work for you as well.

---

### Post by OMG POTATOE on 2009-05-19
I have a Juke as well, which also worked fine in 8.10, but file transfer between the filesystem and the device is now broken. It seems that we have a regression bug here. 

I have also been able to transfer music to it via banshee, but plugging in the player while banshee is already open causes banshee to freeze for me. I'd like to find a better solution, particularly because banshee is also somewhat buggy for me and not all of the media that I'd like to load onto the device is currently in banshee's library.

In 8.10, this device was automatically mounted to /media/TELECHIPS (I think), but it no longer seems to be mounted to the filesystem when plugged in. I can access it via the gnome gui, but am unable to transfer any files to it, encountering the same problem as the original poster. Does anyone know of a way to manually mount the contents of this device to a location on the file system?

---

### Post by Orfintain on 2009-05-24
Thanks Surfpup banshee is doing the trick.

I still haven't been able fix nautilus 

"Could not open location 'file:///home/user/Documents'"

"Failed to execute child process "rhythmbox" (No such file or directory)"

I have uninstantiated rhythmbox..

---

### Post by Orfintain on 2009-05-24
Or at least it usually works sometimes I get this error 

"LIBMTP_Send_Track_From_File_Descriptor(): subcall to LIBMTP_Send_File_From_File_Descriptor failed.

---

### Post by maxpowers43 on 2009-08-30
64 bit jaunty, and 9.04 netbook remix. neither will truly mount. recognizes the device, shows up in gnome device manager, has a snazzy desktop icon, but won't tranfer files via any method i've tried, won't open files. any way to change a value in gnome device manager to make the juke truly mount. any suggestions?
thanks in advance

---

### Post by DariusS on 2009-09-22
Hey guys, I too have a Samsung Juke, and I've been using Rhythmbox for a while to sync music to it. While this solution works ok, I'd prefer to navigate through my music on the phone in the same manner as you would with all USB devices. This was the case in the previous Ubuntu distro, and I think I've found the difference.
I just uninstalled the libmtp library (synaptic) and Rhythmbox as well (it is dependent upon the library). Now, when I plug in my Juke, it opens as a USB drive :)

Hope this helps!

---

### Post by DariusS on 2009-09-23
Update to above post: This method does not actually work. It may have potential, but the Juke only appears to function as a USB thumb drive. I was unable to transfer any files to or from the device.
Sorry for the misinformation.

---

### Post by twistdhood on 2009-10-25
I also suffer from this 'break' in compatibility. From my research I believe it has something to do with gvfs. The filesystem is labeled as rw- in my home directory, I can browse under ~/.gvfs/usb%gphoto..., but cannot touch/write/edit/remove the files there. I believe this is some type of restriction/error with gvfs, but dont' have the time to really debug. I hope this helps someone out there with a solution.

here is the mount entry...

```

gvfs-fuse-daemon on /home/hudish/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=hudish)

```

I can confirm, since I've never used/installed banshee before, that the suggested work around does in fact work. It's a little different for me. You have to import your music to a banshee library and then use the banshee interface to drag the music to the Juke, but it got the job done.

I do hope the old usage can return. I scanned my logs while trying to edit the file system and no errors were thrown, from either nautilus or command line. I tried chmod, touch, mv, cp, about everything I could think of and nothing. Interestingly enough, touch, provided this...

```

hudish@cabernet:~/.gvfs/gphoto2 mount on usb%3A001,012$ touch test
touch: cannot touch `test': No such file or directory

```


Like I said, I don't really have the time or energy to do any more than this, plus I'm not familiar with the gvfs to do any good anyways. So, good luck to those who can!

--edit
By before, I mean in Ubuntu 8.10...so my diagnosis is, I could browse/edit/move files just fine in Ubuntu 8.10. I have since upgraded to 9.04 and now the operations described above fail.

---

### Post by jtgd on 2010-01-10
> **DariusS said:**
> Hey guys, I too have a Samsung Juke, and I've been using Rhythmbox for a while to sync music to it. While this solution works ok, I'd prefer to navigate through my music on the phone in the same manner as you would with all USB devices. This was the case in the previous Ubuntu distro, and I think I've found the difference.
I just uninstalled the libmtp library (synaptic) and Rhythmbox as well (it is dependent upon the library). Now, when I plug in my Juke, it opens as a USB drive :)

Hope this helps!

Thanks DariusS, that worked for me.  I could see juke in Nautilus, but copying failed.  I uninstalled libmtp (which dragged Banshee and Rhythmbox out with it) and rebooted.  No problem since I don't use those apps.  It now automounts as /media/TELECHIPS as it used to and I can copy to juke.

I seem to get errors when I umount, but it still seems to work.

---

### Post by Martym on 2010-08-01
I realise that this is probably old news but I could not find anything really useful out in the internets.  A couple discussions around MTP gave me the clue I needed.  It's really dead easy using Gnome.  I am on Ubuntu 10.04

1.  Plug your phone in with the USB cable.
2.  On your phone go to tools & Settings
3.  Press the pound key (#) and enter the code "000000" (unless you have changed this)
4.  Go to option 3, MTP setting
5.  Highlight MTP and press OK, a window will pop up, put the phone down.
6.  Ubuntu will mount /media/TELECHIPS
7.  Navigate to Music, drag and drop till you cannot anymore
8.  When done, click ok on your phone and it will unmount/disconnect.
9.  Enjoy your tunage.

---

