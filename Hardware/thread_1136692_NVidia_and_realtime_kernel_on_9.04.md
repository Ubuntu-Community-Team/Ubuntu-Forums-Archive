---
title: "NVidia and realtime kernel on 9.04"
date: 2009-04-25
forum: Hardware
---

### Post by Le Farfadet Spatial on 2009-04-25
Hello everybody out there!

   I am sorry, but I cannot find the thread I have started one year ago, so I start a new one.

   So, since one year, I cannot use NVidia proprietary driver on the real time kernel. The thing is that I need both OpenGL and real time. I come here, asking if someone has been able to solve this problem. By the way, if someone knows when the open driver Nouveau will be usable, I would be glad to learn about it. If there is nothing to do for now on, is there some way to ask NVidia to solve this problem?

   My configuration:

      -- Dell Latitude D820 laptop;

      -- processor Intel Core 2 Duo T7200 (2.0GHz 667MHz FSB);

      -- bi-canal ram 2x1024Mo DDR2-SDRAM 533MHz;

      -- NVIDIA Quadro NVS 110M 256MB graphic card;

      -- 15.4" WSXGGA+ (1680 x 1050) LCD screen;

      -- 100Go SATA (7200 TPM) hard-drive;

      -- 8x DVD +/- RW burner;

      -- long time battery 9 cells 85 WHr LI-ION;

      -- Bluetooth card for Latitude;

      -- Intel PRO/Wireless 3945 802.11a/g;

      -- Ubuntu Linux 9.04 Jaunty Jacktalop desktop 64 bits.

   Best regards.

                                                        The Spatial Sprite

---

### Post by Le Farfadet Spatial on 2009-04-26
Hello everybody out there!

   I try and up this thread, as it is quite important for me: it is now a year since I cannot use my computer for what I have bought it for. Has anybody any idea? Is there any chance that EnvyNG can install a driver that will solve the problem --- as this Ubuntu release is quite new, there is probably no new stable driver available?

   Best regards.

                                                          The Spatial Sprite

---

### Post by bonestonne on 2009-04-26
I would suggest trying the 32bit version of ubuntu, as drivers for x64 are always buggy for a while.

x86 is more stable anyway, and given the hardware you're using, you'll have the same performance. 2gb of RAM and only a dual core CPU wont have any gain using 64bit over 32bit.

---

### Post by Le Farfadet Spatial on 2009-04-26
Hello everybody out there!

> **bonestonne said:**
> I would suggest trying the 32bit version of ubuntu, as drivers for x64 are always buggy for a while.

x86 is more stable anyway, and given the hardware you're using, you'll have the same performance. 2gb of RAM and only a dual core CPU wont have any gain using 64bit over 32bit.

Thank you for replying.

   The reason I am using the 64 bits version is not for performances, but because as a Ph.D. candidate I am doing developments on 64 bits architectures ([http://www.legos.obs-mip.fr/~lebars/]("http://www.legos.obs-mip.fr/~lebars/")). As a consequence, I want to try my codes on a 64 bits architecture when I am working on my laptop. So I will prefer a solution on 64 bits architecture.

   Best regards.

                                                        The Spatial Sprite

---

### Post by steveneddy on 2009-04-26
Have you tried going back to the 8.04 versions (LTS - Hardy) or the 8.10 version?

These may be more stable than the 9.04 version.

---

### Post by Le Farfadet Spatial on 2009-04-27
Hello everybody out there!

> **steveneddy said:**
> Have you tried going back to the 8.04 versions (LTS - Hardy) or the 8.10 version?


I have been able to use the proprietary driver on 64 bits version with real time kernel on Ubuntu 7.10. The bug with real time kernel appears on Ubuntu 8.04, and occurs on 8.10.

   Actually, I was hoping that Ubuntu 9.04 will solve it.

   Best regards.

                                                        The Spatial Sprite

---

### Post by WestCoastSuccess on 2009-04-28
I can tell you I've been using 8.04 with the real time kernel and the proprietary nvidia drivers successfully since 8.04 was released. I haven't tried 8.10 or 9.04 since I specifically want the LTS version.

Sorry, that probably doesn't help, and I have a different card than you, but thought I'd let you know it is possible, at least with my 7600GS card.

---

### Post by Le Farfadet Spatial on 2009-04-28
Hello everybody out there!

> **WestCoastSuccess said:**
> I can tell you I've been using 8.04 with the real time kernel and the proprietary nvidia drivers successfully since 8.04 was released. I haven't tried 8.10 or 9.04 since I specifically want the LTS version.

Sorry, that probably doesn't help, and I have a different card than you, but thought I'd let you know it is possible, at least with my 7600GS card.

Yes, I know: for most NVidia cards, the driver work perfectly well. But not for mine. The driver does not work correctly with Quadro NVS on real time kernel.

   Best regards.

                                                        The Spatial Sprite

---

### Post by Le Farfadet Spatial on 2009-05-15
Hello everybody out there!

   Today's update have solved the problem: the end of a year of nightmare!

   How can I add a mark-up indicating that this problem is solved?

   Best regards.

                                                          The Spatial Sprite

---

### Post by Zimmer on 2009-05-15
[http://ubuntuforums.org/showthread.php?t=1158191&highlight=mark+thread+solved](http://ubuntuforums.org/showthread.php?t=1158191&highlight=mark+thread+solved)

:)

---

### Post by Le Farfadet Spatial on 2009-05-16
Hello everybody out there!

   Thank you, Zimmer, but when I edit my initial post, I cannot modify the title. Well, to be more specific, I can modify the title of my message, but not of the whole thread. I do not understand what I am doing wrong.

   Best regards.

                                                          The Spacial Sprite

---

### Post by Zimmer on 2009-05-16
I see what you mean, but there is a possibility that when YOU are editing YOUR thread that there will be an option to do this under Thread Tools...

I have never started a thread so I do not have one to hand I could experiment with :)

---

