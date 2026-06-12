---
title: "Update from 8.10 to 9.04: Can't boot..."
date: 2009-05-10
forum: Installation &amp; Upgrades
---

### Post by BEND IT 7 on 2009-05-10
Ok.

I think my last thread was a bit unclear as to what I meant, exactly.

Yesterday, I updated my Ubuntu OS from 8.10 to 9.04.  The update went very smoothly (everything downloaded and upgraded without any error messages).  However, when I went to restart the computer, the farthest I made it was to the login screen.  I then entered my username and password, and all I was left with was a blank screen.  Nothing.  Nada.  I have no idea what to do, and I am super upset about this.

I am stuck using my Win Vista partition (ARGH!), and I would appreciate any help ASAP!  
Thanks.

---

### Post by overdrank on 2009-05-10
> **BEND IT 7 said:**
> Ok.

I think my last thread was a bit unclear as to what I meant, exactly.

Yesterday, I updated my Ubuntu OS from 8.10 to 9.04.  The update went very smoothly (everything downloaded and upgraded without any error messages).  However, when I went to restart the computer, the farthest I made it was to the login screen.  I then entered my username and password, and all I was left with was a blank screen.  Nothing.  Nada.  I have no idea what to do, and I am super upset about this.

I am stuck using my Win Vista partition (ARGH!), and I would appreciate any help ASAP!  
Thanks.

Please do not create multiple threads on the same issue.
What is the model of the graphics card and have you tried booting into recovery mode and using the xfix option to correct the graphics issues?

---

### Post by BEND IT 7 on 2009-05-10
It's an intel graphics media accelerator 950...not the fastest but it runs vista and ran the ubuntu 8 series fine.    I tried that but will try it again.

---

### Post by Shane11 on 2009-05-10
Same problem here, just upgraded from 8.10 to 9.04 and now all I get is a blank screen. Been using Ubuntu since 5.04 on this same set up so don't think it is a hardware issue. Any helpful hints appreciated.
Currently running from the 'live 8.04 disc' - it's the only way I can get on!

---

### Post by Wartender on 2009-05-10
same problem here... more or less. my laptop has a Radeon HD 3200 integrated and it was running 8.10 fine. i upgraded to 9.04 and when i restarted after the loading bar the screen was jumbled up (it displayed the loading bar all weird), hewever, it still worked, the noise of the login screen played, i entered my username and password, and it logged in fine (with the screen not changing from the messed up loading bar). this only hAppened with the 28 kernel, if i booted into 27 it went fine. Then i tried updating the graphics card driver to the latest version and during the update it randomly went back to the login screen. i restarted and the same problem happened with my 27 kernel as well. i went into recovery in the 28 kernel and tried xfix. now it works less. no sounds play and i can't even log on blindly. help?

---

### Post by BEND IT 7 on 2009-05-10
Boot problem solved:

Grub lists 9.04 as four seperate bootloaders (2 and their recovery modes, respectively).  By choosing the second of the two primary bootloaders, I was able to load into Ubuntu.

Now, there are still some graphics bugs, but that's for a different thread.

---

### Post by Wartender on 2009-05-10
someone help me?

---

### Post by overdrank on 2009-05-10
> **Wartender said:**
> someone help me?

You may look [here]("http://ubuntuforums.org/showthread.php?t=1152992")
Edit correct link :oops:

---

### Post by Wartender on 2009-05-10
what do you mean? you linked me to the same thread... i know ati cards are buggy but this wasn't happening before. i could try reconfiguring my xserver but i forgot the terminal line
something like dpkg -reconfigure xserver-xorg?

---

### Post by Wartender on 2009-05-10
i have just noticed around the forums that jaunty apparently has issues with ATI cards. great. can i downgrade from the terminal of the recovery?

---

### Post by virLudens on 2009-05-10
ah, I've been having this problem as well. Can I uninstall the driver from the terminal in recovery mode then?

---

### Post by BEND IT 7 on 2009-05-11
Yes wait...not working, still.  Is there a way to donwgrade to 8.10 from recovery?  Please...using Windows is so annoying.

---

### Post by Wartender on 2009-05-13
somebody please? bump...

---

### Post by Wartender on 2009-05-13
help... please. i'm going on vacation in less than 2 weeks ad i need my laptop to work. i really don't want to do a clean reinstall! help!

---

### Post by Wartender on 2009-05-14
somebody please help. does noone know what to do?

---

### Post by Wartender on 2009-05-16
help...

---

### Post by Wartender on 2009-05-17
come on guys! please! :(

---

### Post by Wartender on 2009-05-18
i'm leaving in 2 days and i NEEd my laptop to work! is there any way to downgrade without losing all my stuff?

---

### Post by Wartender on 2009-05-19
heeelp.... pleeeeeease... i guess i'll just have to clean reinstall intrepid
... or go back to windows D:

---

### Post by BEND IT 7 on 2009-06-10
I just uninstalled by manually deleting the partition from Windows and then installed 8.04 (Hardy), the LTS release, on that partition.  Hardy had worked flawlessly before, and since it will be supported for a long time by the makers of Ubuntu, I have decided to stick with it.  I do not need the latest version, especially if it is not going to work right on my hardware.

Besides, 8.04 "Hardy Heron," as an LTS release, should by default be the most trustworthy and stable version of Ubuntu until the next LTS release.

I'm happy with Hardy.  :D

---

