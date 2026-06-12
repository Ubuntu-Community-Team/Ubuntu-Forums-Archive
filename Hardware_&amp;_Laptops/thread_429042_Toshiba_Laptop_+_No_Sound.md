---
title: "Toshiba Laptop + No Sound"
date: 2007-04-30
forum: Hardware &amp; Laptops
---

### Post by sfitch29 on 2007-04-30
Hello, I am new to Ubuntu and Linux in general.  I have a Toshiba Satellite A205-S4577 Laptop, on which I just installed Ubuntu Linux 7.04 - everything is going well, WiFi is working great, but I have no sound.

I have adjusted the sound preferences to be optimal, but I still have no sound.  I would appreciate any help.

Thank You.

---

### Post by DagMan on 2007-05-01
This has worked for a lot of toshiba laptop users
[http://ubuntuforums.org/showthread.php?t=416207](http://ubuntuforums.org/showthread.php?t=416207)

---

### Post by davin on 2007-05-01
on my  toshiba laptop sound not working. i tried  2~3 version of ubuntu but none of them worked.

---

### Post by venky80 on 2007-05-27
> **sfitch29 said:**
> Hello, I am new to Ubuntu and Linux in general.  I have a Toshiba Satellite A205-S4577 Laptop, on which I just installed Ubuntu Linux 7.04 - everything is going well, WiFi is working great, but I have no sound.

I have adjusted the sound preferences to be optimal, but I still have no sound.  I would appreciate any help.

Thank You.
same laptop same problem
******* intel HD audio

---

### Post by Sir_Leon on 2007-06-04
> **sfitch29 said:**
> Hello, I am new to Ubuntu and Linux in general.  I have a Toshiba Satellite A205-S4577 Laptop, on which I just installed Ubuntu Linux 7.04 - everything is going well, WiFi is working great, but I have no sound.

I have adjusted the sound preferences to be optimal, but I still have no sound.  I would appreciate any help.

Thank You.

Same laptop, same problem :( 
and i am about to be crazy... :((((

---

### Post by SwannyJ on 2007-06-23
I have the 4587, same problem.  Everything else works great...wish I could find a fix.

---

### Post by skeetre on 2007-09-16
Using the new 2.6.23rc kernel, and new ALSA 1.0.15rc, I have sound with my Toshiba A205-4607 laptop!

---

### Post by lisati on 2007-09-16
What worked on my Toshiba A100 laptop was the following:
[LIST=1]
[*]Install ALL updates
[*]Reboot
[*]Tweak volume control settings
[/LIST]

Hopefully this will help

---

### Post by shawnc_nmb on 2007-09-17
I fixed this problem on my Satellite P205-S6237 with a small tweak.

Now the last thing I noticed was that my sound card wasn&#8217;t working apparently, After abit of googling i found that by simply adding 1 line to the ALSA config it will be fixed sorta. So back in the terminal paste this

[php]
gksudo gedit /etc/modprobe.d/alsa-base
[/php]
Now at the very bottom of the file just add the following
[php]
options snd-hda-intel probe_mask=8 model=3stack
[/php]
Ok, Close and save that file and reboot your computer. you should have a fairly functional Ubuntu Laptop now.

Visit [here]("http://www.shawnc.org/category/linux/page/3/") for more adjusts I made to my Toshiba Satellite.

---

### Post by NoEsAlAzar on 2007-10-21
I tried this with a Satellite A205-24577, but it didn't work :( Any other idea?

---

### Post by crazyforpurple on 2007-10-24
I ahve a toshiba satellite A135-S7404 and today I got my sound working!! below is a list of what i did, I actually got the info from this link:

[http://ubuntuforums.org/showthread.php?t=530374](http://ubuntuforums.org/showthread.php?t=530374)

but below is specificatlly what I did:

hope this helps xxx

love lucy xxx


1. after installing ubuntu gutsy i had no sound and no sound cards were detected.
2. when i tried the command "cat /proc/asound/cards" it would just say no soundcards installed
3. i couldnt even find these files....
"Remove ~/.asoundrc and ~/.asoundrc.asoundconf."

let alone remove them! so i went on to the next step:

4. i then went onto your next step:
"Install Ubuntu kernel back ports (linux-backports-modules-* ). You may need to run the above command (Possible conflicting driver issue). Then reboot."

to do this i did the following:

go to system, administration, synaptic package manager,
type in your password
in synaptic package manager, go to settings, repositories

under the "ubuntu software" tab I checked on each entry under "downloadable from the internet" and unchecked the cd/dvd option.

then under the "updates" tab I checked everything including the gutsy backports.
close the repositories box and then click reload in the synaptic package manager.

5. I don't think its necessary at this time but I restarted my laptop for good measure at this point.

6. I then went back into the synaptic package manager and ran a search for backports

7. I also went to applications, accessories, terminal and ran the following command
uname -r to find the details of my kernal.

it came back with 2.6.22-14-generic

8. In the synaptic package manager I had many options from my search and I wasnt sure which one I should use... I narrowed it down to

linux-backports-modules (which in the info said "Generic Linux backported drivers.")
and
linux-backports-modules-gene-2.6.22.14.21 (which in the info said "Backported drivers for generic kernel image")

I'm not quite sure why, but I clicked on the latter on and marked it for install. I then clicked "apply" and once it was all done I restarted the laptop and on restart I had sound!!!!!!


This may not be worth noting but when I use the term "restart" I actually shut down and then start up the laptop as using the "restart" option on mine means that it hangs before the log in screen.

---

