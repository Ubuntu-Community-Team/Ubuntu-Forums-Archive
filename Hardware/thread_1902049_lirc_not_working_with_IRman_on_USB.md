---
title: "lirc not working with IRman on USB"
date: 2011-12-29
forum: Hardware
---

### Post by BenFranske on 2011-12-29
I'm hoping someone here will have some insight. I'm trying to get LIRC working with an old IRman serieal receiver through a USB-Serial adapter and am having some difficulty getting lirc to see any input from the IRman.

Here are some details:
I am using the Mythbuntu packaged version of LIRC, this is version 0.9.0.
The USB-Serial adapter I am using is a Prolific PL2303 based device which Ubuntu udev has located at /dev/ttyUSB0
I have the lines REMOTE_DRIVER="irman" and REMOTE_DEVICE="/dev/ttyUSB0" in my /etc/lirc/hardware.conf file.

When I run "irrecord test3" I get:
irrecord -  application for recording IR-codes for usage with lirc
Copyright (C) 1998,1999 Christoph Bartelmus(lirc@bartelmus.de)
irrecord: could not get file information for /dev/lirc
irrecord: default_init(): No such file or directory
irrecord: could not init hardware (lircd running ? --> close it, check permissions)

When I run "irrecord -d /dev/lircd test3" it starts normally but sees no ir codes coming in.

When I run  "irrecord -H irman -d /dev/ttyUSB0 test3" everything works exactly as it should and I can read in IR codes and create the "test3" device file but of course lirc is unable to see the commands (and irw doesn't show any input) when tested.

When I run "lircd -H irman -d /dev/ttyUSB0 -n" the daemon starts up and when I open up irw in another terminal I see that lircd has accepted a new client but I still see no ir commands being received.

Suggestions/thoughts?

Thanks!
-Ben

---

### Post by daworm666 on 2012-02-19
I just registered hoping to find the answer to the exact same question.  Since your question has gone so long without an answer, I suppose we're both out of luck.

I can say that I managed to build lirc from source, and starting it manually I can get irw to recognize key presses, but I can't for the life of me figure out how to make it load properly on its own.  I try "sudo /etc/init.d/lirc start" and nothing happens.  I've double and triple checked my /etc/lirc/hardware.conf" file.  Very frustrated.

---

### Post by BenFranske on 2012-02-20
I actually joined one of the lirc official mailing lists to see if I could get any help. No one there could assist me either. Even though the irman is listed as supported hardware I guess I'd call it legacy and say it's not really supported anymore and all the devs have moved on to newer hardware. 

Just to close the loop I ended up going out and purchasing a new USB Microsoft Media Center Extender compatible remote receiver and remote for about $30. It works beautifully as an lirc receiver with all my existing remotes (and the one it came with isn't bad either) so that's my suggestion.

---

### Post by daworm666 on 2012-02-20
Unfortunately, the very expensive A-Tech Fabrication case I bought back in my bachelor days is made to custom fit the IRMan.  Don't even get me started on LCDProc and the Griffin PowerMate...

---

### Post by daworm666 on 2012-02-20
With a bit of perseverance, I have it working, in case anyone else comes looking.

Here's a bare bones guide that should get you through it.  All of this might not be necessary, but it works.

1. cd ~
2. sudo apt-get install lirc
3. sudo apt-get source lirc
4. sudo apt-get install dpkg-dev
5. sudo dpkg-reconfigure lirc
    Pick Irman/UIR from menu
6. sudo /etc/init.d/lirc stop
7. irrecord --driver=irman --device=/dev/ttyUSB0 -n lircd.conf
    In the above, substitute the port you are using for where I used my USB serial adapter
    Follow all the prompts, use key names from known conf file so other thinks like the rc file match.  Mine was a Hauppage_350
8. nano lircd.conf
    Change the remote name to the name of the one you copied the key names from
    Ctrl-X to save
9. cp lircd.conf lircd.conf.backup
    A backup never hurts
10. sudo cp lircd.conf /etc/lirc/lircd.conf
11. sudo nano /etc/lirc/hardware.conf
     Change REMOTE="whatever" to the remote name you put into lircd.conf
     Make sure REMOTE_MODULES=""
     Make sure REMOTE_DRIVER="irman"
     Make sure REMOTE_DEVICE="/dev/ttyUSB0" or whichever port you are using
     Ctrl-X to save
12. sudo /etc/init.d/lirc start

13. To test
     /usr/bin/irw  (have to type path, or at least I did)
     Ctrl-C to exit

Hope this helps someone else down the road.

Jeff.

---

