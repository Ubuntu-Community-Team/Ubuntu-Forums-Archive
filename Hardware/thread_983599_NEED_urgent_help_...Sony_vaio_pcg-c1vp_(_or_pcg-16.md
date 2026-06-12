---
title: "NEED urgent help ...Sony vaio pcg-c1vp ( or pcg-161L)?"
date: 2008-11-15
forum: Hardware
---

### Post by sieger007 on 2008-11-15
Any kind of help from someone who has this is......... much appreciated a lot.......
I have a pcg-c1vp . The bios shows some like shadowed - I think.
When I go to the boot order options it does give a drop down to change the boot order . I put Removable Devices > CD ROM > HD in that sequence.
In Spite of that it will NOT RECOGNIZE my UBUNTU  or XP CD ROM   DVD on an external DVD RW and simply comes to the OS Menu.
How do you get this puppy to recognize the bootable windows drive ?

---

### Post by pytheas22 on 2008-11-16
I don't have this motherboard, but...

Are you sure your CD/DVD drive is installed and working?  You may want to try swapping in a different one if you're not positive that it works.  You could also try reconnecting the cables.  Or disconnect the hard drive so that it has no other option than to boot to CD (I know you probably need the hard drive connected since you probably want to install something on it, but this would at least let you know whether the CD drive works).

Also, most modern BIOS programs will let you open up a boot menu.  Have you tried selecting the boot device this way instead of by setting the boot order in the BIOS configuration?  If you press the pause/break key at your BIOS screen, it should pause so that you can read the different options and figure out which key you need to press to get a boot menu.

---

### Post by sieger007 on 2008-11-23
THANKS  for the quick help
As per this forum 
[http://www.farstand.com/cgi-bin/pcg-c1/Forum.exe](http://www.farstand.com/cgi-bin/pcg-c1/Forum.exe)
The thing refuses to boot of ANY CD Rom execpt a PCMCIA CD or FDD  ...I dont know if there is any other viable alternative.... but to buy that off for $40+.
But suppose i get a PCMCIA FDD , then  how should I proceed to install DSL on the Computer.

Thanks and happy Thanksgiving. 
Sam

---

### Post by pytheas22 on 2008-11-23
I didn't know you were only trying to install DSL, but if that's the case, you're in luck.  It's possible to [install DSL even if you can only boot to floppy]("http://damnsmalllinux.org/wiki/index.php/Floppy_Only_Install_(No_Netcard,_Linux_Only)") (you will need a working CD drive too, but it doesn't have to be bootable).  It's not very fun, but it's possible.

Also, if you have Windows installed already on this machine, you could put a Linux on it from within Windows by using [unetbootin]("http://unetbootin.sourceforge.net/").

Finally, it's a bit bizarre that your BIOS thinks that it should be able to boot to CD, but refuses to do so.  I've seen older computers that don't have the ability to boot to CD at all just because BIOS doesn't support it, but anything made withing the last ~ten years should boot to CD.  You should make sure that the CD drive itself is just not broken, and if you're adventurous, you could take the computer apart to make sure all of the connectors are properly inserted, etc.

---

### Post by sieger007 on 2008-11-23
Thanks again. That was really  useful information.  Actually I  like the looks for this puppy C1VP  ( just about  the the size of my toothbrush  and as thick than a Frid evening standard crust Dominos , w/ a Webcam but it does NOT have an internal CD Drive. Should have mentioned that earlier.   )   and was desperately interested in hauling in DSL/Kubuntu  the least.   I might be  totally mistaken , but,  from whatever appears on those dedicated pages made by Vaio Geeks , the PC is made   to boot from ONLY  from a PCMCIA CD not a USB CD.  I actually have an External DVD writer (  using which I burnt these iso images  - so that works well ) which I hooked up to its usb port . Its Identifies that  well. I then hooked up the same to a PCMCIA adapter w/ a USB port so that I could 'pretend' in making it boot off a PCMCIA CD - Does not work. So in other words this works only with that propriety PCMCIA CD. BTW the BIOS gives a message "Shadowed" . I went to update it and it needs update via a bootable  (= PCMCIA ) cd/FDD  not any other way. Strange ...?  but  looks like thats happening.
I never knew they had a concept of  Linux being booted off a Windows Machine...is it possible for me to use it to modify a Grub entry that already exists ?  .


 Elsewhere......I have ASUS F3SV  where I want to install 4 flavors of linux + 2 Windows  ( xp and vista ) . I Installed 2 Linuxes ( OpenSuse 11 and Kubuntu ) and all the crapsoft ...   already and 2 more linux  remain. 1 such remaining one is DSL Linux and other is Feather or puppy . I have created their partitions already using /ext3 . But the problem is that When I boot the Live DSL CD and use Grub Frugal method , it does not  see my /ext3 partition ( I tried hda9 and sda9 none of them work ) and gives error .  I wonder what the problem here is . Nonetheless ,Sir I sure want to check out that Ubootin tool if it solves all problems once and for good.
Thanks again
Bye
Sam

---

### Post by pytheas22 on 2008-11-24
> I never knew they had a concept of Linux being booted off a Windows Machine...is it possible for me to use it to modify a Grub entry that already exists ? .


I think that unetbootin actually doesn't deal with grub if you use it on a Windows machine; it just modifies the Windows boot menu to allow it to boot Linux.  But you should be able to install one of numerous different Linuxes using unetbootin, as long as you have a working Windows system to start with.

As for the ASUS F3SV, I'm not sure what's going on.  But the best thing might be to boot to an Ubuntu live CD, install gparted (by typing 'sudo apt-get install gparted'), then launch gparted to see the partition structure of your disk.  gparted has a nice graphical interface that should make it easy to see all the different ext3 partition and note the names assigned to them.

Also keep in mind that just because you have nine partitions on your disk, the last one is not necessarily sda9.  It could be any number.

---

### Post by sieger007 on 2008-11-24
Hi and Many Thanks again.
Well actually I used Yast2 on Suse to see all my partitions on the  ASUS and they all look good. 
I created some  x4  - ext3 partitions and 1 common swap partition. Out of that I installed openSuse11 ( Gnome based facility ) and Kubuntu ( KDE based GUI ) so far. 

Now when I boot the live DSL cd , and choose frugal grub method , and give exact path of Partition /dev/sda9
it says it does not exist or something like that. I am still curious to know what is the problem . Why wont it install the image to /dev/sda9 or hda9 whatever it wants to call that .That   Mounting  fails , too...
mount -t /ext3 /dev/sda9 /<somepoint>  
<so such drive or something >

So I was trying to figure that out , when I got this breakthrough suggestion of doing a DSL install via my Windows partition. 
I wonder if I could get ubootein to write the entry onto grub than the windows bootloader.
If not then I guess,  I have to append them to the boot.lst of the 1st grub entry .
But there the problem is each OS may have a different default to start up. how do I figure that out ?...
thanks
Sam

---

### Post by pytheas22 on 2008-11-24
> Why wont it install the image to /dev/sda9 or hda9 whatever it wants to call that .That Mounting fails , too...

If you've verified that the partition definitely exists, the problem could be that the DSL kernel (which is quite old) doesn't include a driver for your hard drive--this can happen with newer drives.  Is DSL able to see any partitions on the disk?

It's also possible that for some reason DSL doesn't see the partition as /dev/sda9 even though SUSE does.  DSL may be giving it a different name.  If you can get to a command prompt anywhere in DSL, type:
```

ls /dev | grep -e sd -e hd
```

This should give you a list of all disk partitions that DSL is able to see.

> So I was trying to figure that out , when I got this breakthrough suggestion of doing a DSL install via my Windows partition.
I wonder if I could get ubootein to write the entry onto grub than the windows bootloader.
If not then I guess, I have to append them to the boot.lst of the 1st grub entry .
But there the problem is each OS may have a different default to start up. how do I figure that out ?...

You shouldn't have to worry about the grub menu at all.  As long as you can boot into Windows, unetbootin should be able to set up the Windows boot menu so that you also have the choice of booting into Linux--and you can have more than one Linux on the Windows boot menu.

---

