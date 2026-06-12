---
title: "ubuntu 8.10 doesn't boot from live cd or by installing it"
date: 2009-02-21
forum: Installation &amp; Upgrades
---

### Post by colifato13 on 2009-02-21
hi, I need help getting ubuntu 8.10 to boot. I already try installing it and from the live cd, but i had no luck.

when i try installing it I get the following errors.

    132.151213 end request I/O error, dev sr0, sector 1431720
    132.151269 Buffer I/O error on device sr0, logical block
    178965
    [COLOR="Blue"](this keeps going until it gets to the 600s)[/COLOR]
    
  After that I get this:
    The display server has turn of 8 times in the last seconds
    [COLOR="Blue"](this keeps going forever, i think, i didn't check)[/COLOR]

When i try using the live cd i get the following errors.

    132.151213 end request I/O error, dev sr0, sector 1431720
    132.151269 Buffer I/O error on device sr0, logical block
    178965
        [COLOR="Blue"](this keeps going until it gets to the 600s)[/COLOR]

  After that all i get is a brown screen and that's it, nothing
  happens

I read somewhere in this forum that it was because the drives were set to cable select (which they were), i alraedy set them to master and slave but i keep getting the same errors.

any help would be appreciated, thank you

---

### Post by Pumalite on 2009-02-21
Bad burn or bad burner. Clean the lens. Burn a new CD at 4x or slower.

---

### Post by networm1230 on 2009-02-21
hello. I have try to do burn a ISO file of ubutu 8.10 to a CD is will burn the ISO. it says burn complete and to pleas insert the burn CD back in to check if the files burned to the CD avry thing seems OK. I rein ubutu 8.10 live CD and when I try to install the CD ubutu 8.10 or try to test drive it dos not work. but when i do a CD integrity test it passes the test. Any help!

---

### Post by networm1230 on 2009-02-21
> **colifato13 said:**
> hi, I need help getting ubuntu 8.10 to boot. I already try installing it and from the live cd, but i had no luck.

when i try installing it I get the following errors.

    132.151213 end request I/O error, dev sr0, sector 1431720
    132.151269 Buffer I/O error on device sr0, logical block
    178965
    [COLOR="Blue"](this keeps going until it gets to the 600s)[/COLOR]
    
  After that I get this:
    The display server has turn of 8 times in the last seconds
    [COLOR="Blue"](this keeps going forever, i think, i didn't check)[/COLOR]

When i try using the live cd i get the following errors.

    132.151213 end request I/O error, dev sr0, sector 1431720
    132.151269 Buffer I/O error on device sr0, logical block
    178965
        [COLOR="Blue"](this keeps going until it gets to the 600s)[/COLOR]

  After that all i get is a brown screen and that's it, nothing
  happens

I read somewhere in this forum that it was because the drives were set to cable select (which they were), i alraedy set them to master and slave but i keep getting the same errors.

any help would be appreciated, thank you

I have the same problem with burning iso ubutu 8.10

---

### Post by networm1230 on 2009-02-21
> **Pumalite said:**
> Bad burn or bad burner. Clean the lens. Burn a new CD at 4x or slower.

I burned the ISO ubutu 8.10 at 1x and still nothing

---

### Post by Pumalite on 2009-02-21
Try your CD in a different computer. I think your next suspect is the burner.
[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28)
Don't forget to do md5sum on the iso prior to burning.

---

### Post by colifato13 on 2009-02-23
I'm sorry i took this long to post but i had problems with my connection.

I don't think that the drive or cds are the problem, because i already try with two drives, i burned different copies, and i check the cds for errors, and everything seems fine. I even try with the alternate version.

This thread [http://ubuntuforums.org/showthread.php?t=1015569]("http://ubuntuforums.org/showthread.php?t=1015569") said that the problem was solve, but i tried everything that there is to try with the jumpers.

about the display server turning off i think there is a problem with my intel graphics driver, because on intel's site there aren't any drivers that match mine, instead it says that they were made by compaq.

i don't think that I'll be using ubuntu anytime soon, but it was cool seeing the splash. haha

thank you, for helping

---

### Post by karthie on 2009-02-23
hey
i had the same problem with the live CD
why dont you try to burn the image in a DVD instead of cd and make sure that you don burn the image directly use any software that will read and unpack all the contents inside the image.and then burn the files unpacked bu the image burner it might work 
coz it worked for me thats why suggesting you the solution 
thank you

---

### Post by colifato13 on 2009-02-23
hey i was just reading about that, I'm going to try it right now, hopefully it works. Thank you for posting it!!!

Do you think that powerIso is good, or should try something else?

---

### Post by bertolo on 2009-02-23
this is nothing to do about the burn. i got the same problem in some pc's. it's because of the hard disk.

---

### Post by colifato13 on 2009-02-23
is there a way to fix it, because right now i got to wait like 10 minutes for it to get close to booting.

From what i had read, I think that the errors i'm getting have nothing to do with ubuntu not booting up, except for the"display server has shutdown 8 times....".

I think that i got a problem with my graphics driver.
but i don't know how to install them.

thanks

---

### Post by Pumalite on 2009-02-23
Post:
```
dmesg
```

---

### Post by colifato13 on 2009-02-23
hey _pumalite_ i can't understand you.
can you explain it a little more.
thanks

---

### Post by Pumalite on 2009-02-23
Boot your Live CD and, from the Terminal; post:
```
dmesg
```

---

### Post by colifato13 on 2009-02-23
Thank you _Pumalite_
you just save a lot of time.

Here is a explanation of dmesg if anyone is interested
[http://linuxgazette.net/issue59/nazario.html]("http://linuxgazette.net/issue59/nazario.html")

---

### Post by kamolt on 2009-02-23
Exactly the same problem occurred here. I disconnected the hard drive and the problem remained, so the hd was not to blame. The I tried to boot from 8.04 and surprisingly that worked fine. Then I replaced the DVD drive with a newer one and YES 8.10 booted and installed also. Obviously in my case Intrepid was more DVD drive selective then Hardy. Not completely illogic...

---

### Post by colifato13 on 2009-02-23
hey kamolt I was going to try that a while ago but i didn't had any, to bad i'm going to have to wait until tomorrow.

does it matter at what speed you burned it?

---

### Post by kmacphail on 2009-02-23
I had no problems installing Ubuntu 8.10 on my machine, but my wife and another friend did.  The quick(est) way I found to go around this was by installing Ubuntu 8.10 through a bootable USB memory stick. Oddly enough both problems were on laptop computers but it installed fine on my desktop.

To do this you need a stick with 2GB memory.

**To do this in XP:**

Make sure the memory stick is in the computer

Download this file [u810p.exe]("http://www.pendrivelinux.com/downloads/u810/U810p.exe")

Extract this and it will create a folder called **U810p**.

Place the Ubuntu 8.10 disc image (the iso file) into this folder.

Double click on u810.bat and follow all on screen instructions.

**To do this from the UNetbootin**

Download UNetbootin

Make sure that you have the Ubuuntu 8.10 disk image file (iso) and your memory stick in the computer

Load UNetbootin, 
click on **diskimage** 

then on the opposite side of the screen **click on the ... button**

**select the iso file **and press enter (or double click)

Make sure **your memory stick is selected **at the bottom of the screen and click OK

After UNetbootin has finished you can select **Reboot Now**.

Please not that for this method to work your computer must be able to boot from USB devices.  Your USB device must also be selected as your first device in the boot up list.  To alter the boot list you will need to press a button at the startup screen immediately when the computer is switched on.

I am sorry if this post is a bit tiresome, but I wanted to make sure that anybody would be able to follow these instructions with one step rather than spread over a few posts.

I hope this has been of some help.

---

### Post by colifato13 on 2009-02-23
thanks _kmacphail_ you just save me a trip to the store.
I'm going to try this as soon as i can.
do you know if i can partition my drive from the usb like the live cd?

thanks for helping

---

### Post by kmacphail on 2009-02-23
You can do anything from your USB boot that you can do on your LiveCD boot, it is also a bit faster and has an added advantage that stuff can be saved onto the USB stick.

---

### Post by kamolt on 2009-02-23
> **colifato13 said:**
> hey kamolt I was going to try that a while ago but i didn't had any, to bad i'm going to have to wait until tomorrow.

does it matter at what speed you burned it?

I burned my cd's at default speed with brasero, I don't think thats the problem. Before if discovered my old DVD drive was not compatible with 8.10 I did a couple of burns too but none of them worked.Then I put the (not so old) drive I burned the live CD with in the new machine and it worked. 

Nice post from kmacphail, hope this will help you, otherwise a new DVD drive will make you 20$ poorer.

---

