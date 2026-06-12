---
title: "/dev/cdrom but /media/cdrom0 ...what??"
date: 2006-04-21
forum: Hardware &amp; Laptops
---

### Post by jms830 on 2006-04-21
I'm a newbie on these matters.

I have 2 cd drives: the first is a CD-Rom, and the second is a CD/DVD-RW drive.

I have the folders /dev/cdrom/  and  /dev/cdrom1

however, I know that my cd drives are mounted as /media/cdrom**0**/   and  /media/cdrom1/  respectively.

My question is: why don't I have /dev/cdrom0  ?

I feel this may be complicating my attemps to enable DMA on the drives. I maybe need to clean these things up? Any help is appreciated, thanks.

---

### Post by adamkane on 2006-04-21
It's not something to fret over. cdrom is probably  a legacy device name, when no one had a second cdrom, and is probably the same as cdrom0. cdrom1 was probably created to distinguish between the two devices.

---

### Post by jms830 on 2006-04-23
ok, thanks. So in order to turn DMA on for my cd-rom and dvd-rom drives, I would have to put which of the following at the end of my hdparm file? or could I just put all of them and it would work?

/dev/cdrom {
       dma = on
}

/dev/cdrom0 {
       dma = on
}

/dev/cdrom1 {
       dma = on
}

---

### Post by adamkane on 2006-04-23
I've been using Automatix to enable DMA.

This is what I have in my hdparm.conf:

> 
/dev/cdrom {
       dma = on
}


After reading your posts, I added this as well:

> 
 /dev/cdrom1 {
        dma = on
 }
 

I can't tell you yet if this is correct.

I think I've found another piece in Automatix that needs to be fixed though.

---

### Post by Sutekh on 2006-04-23
Use this command
```
ls -l /media
```
You will see that /media/cdrom is a symbolic link (shortcut) to /media/cdrom0.  

There should be similar ones for  /media/floppy -> /media/floppy0 and           /media/usb -> /media/usb0.

 I have no idea why this is...

---

### Post by jms830 on 2006-04-24
thanks for the replies. you are correct about the symbolic links. I am going to try and mess around with the hdparm.conf, Adamkane did adding cdrom1 seem to work out for you? I tried before and my dvd-r wouldn't read things properly.

EDIT:  the command "sudo hdparm /dev/cdrom" and "sudo hdparm /dev/cdrom1" will tell you some info, like if DMA is on, you may already know this of course.

---

