---
title: "EEE 1000 + Sound Reload when Resuming"
date: 2008-08-19
forum: Hardware
---

### Post by Jws0001 on 2008-08-19
Hi guys, I'm still tinkering with Ubuntu on my EEE 1000 and it's been going well but I still have a few kinks to smooth out, this being one of them.

Currently in the wiki from eeeuser there is some documentation on getting the sound to work for the EEE 701/900 models which I have quoted and highlighted below.  Can anyone figure out the small problem documented in this quip that I've highlighted?  Having to click reload every time I resume is a bit annoying.

> Audio after suspend/resume
For some reason the sound doesn't always come back after resuming on EeePc 90x hardware. Alsa needs to be instructed to specifically suspend and resume its own modules before the OS does. 

(Note: this doesn't appear to be a problem under EeePc 70x hardware, or for Gutsy, however I cannot confirm :) 

[COLOR="Red"]**Warning: After applying this hack you may see a warning message after resuming that says the gnome-mixer has quit unexpectedly. Just click the reload button each time, or hit cancel to remove the applet. Currently there is no work-around to this problem.** [/color]

Note: This may not be a 100% solution. After the resuming, the sound device tests work (System –> Preferences –> Sound), audio on applications like Skype work, but the Gnome 'System Sounds' still do not work after resuming even after reloading the mixer (e.g. the 'logout' sound no longer plays). If you log out and log back in again (no reboot needed), the 'System Sounds' do come back, so perhaps some other Gnome item also needs to be restarted.
Source: [http://wiki.eeeuser.com/getting_ubuntu_8.04_to_work_perfectly](http://wiki.eeeuser.com/getting_ubuntu_8.04_to_work_perfectly)

---

### Post by chettyk on 2008-08-19
I have just bought an Eee PC 1000H, which came with Windows-XP preloaded. (The Linux version is not being sold in India.) I would like to load Ubuntu on my Eee PC. So let me ask you how easy/difficult it is to get Ubuntu working on the 1000 series. Some of the posts I have read in the Eee user forum and elsewhere suggest that getting wired and wireless Internet connection working is a bit of a problem. What has been your experience with installing Ubuntu on the Eee PC 1000?

---

### Post by Jws0001 on 2008-08-19
It hasn't been a completely breezy task.  I actually used an installation of eeebuntu which is esentially ubuntu but slightly customized.  I stuck with this distro because it was the most functional out of all the ones that I tried upon initial installation.

Yep, both the internets (wired/wireless) did not work at first.  I wish I had documented every step of my journey but I have not done so.  I know that my EEE has a bookmark somewhere that helped me with at least one of the internet fixes but it took a bit of work to get it going.  I'll try to post the link later when I get home.

Overall it hasn't been too bad.  I was initially able to load up with;
[LIST]
[*]Suspend/Resume
[*]Power/Shutdown
[*]Correct Resolution (1024x600)
[*]Functional Sound
[*]Functional ACPI abilities
[/LIST]
All I really needed to do was correct the internet issues, run a few updates and install a few core applications that I like, and it was good to go.  Right now I have power profiles configured for battery/AC adapter mode and I love it.  It dynamically clocks the CPU and I also have the ability to underclock it on demand to one of 4 speedsteps to save battery or lower the cpu temp (it can get a bit hot at full load and 1.6ghz if left that way for a while).

Edit: The things that I'm still working on are this little sound bug (which isn't a big deal, just an annoyance) and seemless support for an external monitor/projector for presentations.  Linux is much more efficient that Windows IMO and has run much smoother for me.  If I ever do decide to try windows (and I probably wont) I would look to reduce the bulk in every way possible.  Whichever way you go I would recommend 2GB of ram (~$40), especially if you configure linux to not use a page file.

---

### Post by Jws0001 on 2008-08-19
I have some more information for you guys... that is if anyone can help me :P

I've discovered that the thing I'm talking about is the mixer_applet2 and it's an excutable located in /etc/lib/gnome-applets/

How can I load this applet on resume?

I know how to kill it... which I could do on suspend... but what can I put in my resume script to load it automatically?

---

### Post by Jws0001 on 2008-08-20
cmon....

---

### Post by chettyk on 2008-08-20
Thanks for your feedback on installing Ubuntu on Eee PC 1000.

As for the problem you are facing, have you considered posting the question in the Eee User Forum? Maybe someone there has figured out a fix.

---

### Post by Jws0001 on 2008-08-20
I have a similar thread posted there with a similar amount of success :\

---

### Post by foobunt on 2008-09-11
On my xubuntu/eee900 installation the following did the trick:

Add this to /etc/pm/config.d/config
```

SUSPEND_MODULES="$SUSPEND_MODULES snd_hda_intel"
RESTORE_SOUND="yes"

```

Source: [http://forum.eeeuser.com/viewtopic.php?id=31621](http://forum.eeeuser.com/viewtopic.php?id=31621)

---

### Post by Jws0001 on 2008-09-11
This did not resolve my issue.  From reading that source it appears that this fixes the "no sound" when restoring from standby.  My problem is that I ***have*** sound after I restore, however I get an annoying prompt saying that the mixer applet has quit unexpectedly.  I want to automatically reload the mixer applet so that I don't get this prompt every time.

---

### Post by foobunt on 2008-09-12
Why use a workaround to solve your second problem which only exists due to a buggy workaround that solved your first problem?

If you can solve your "no sound after resume"-problem with the modified */etc/pm/config.d/config* you would not need the workaround from the eeeuser-wiki which is forcing the module to be unloaded. 

Module not forced unloading, mixer-applet not crashing, problem solved. :)

---

### Post by Jws0001 on 2008-09-12
I forget where but I believe it does need to be unloaded, it's just done somewhere else.  Without the unload the sound wont work, your unload was probably just redundant, appearing to have no effect.

---

### Post by foobunt on 2008-09-12
Unloading the module is just what it does. :neutral:
 
Figuratively: 
It tells pm-utils to kindly ask the module called snd_hda_intel to leave working memory before suspend. 
Your solution tells alsa to grab a rolling pin, knock off snd_hda_intel and throw it out of the RAM.

I can only say, that it worked for me and since hardware and OS are not that different there is a good chance that it solves your problem.

**_How to proof me wrong in 1 minute:_**

Change back "/etc/default/alsa" from 
*force_unload_modules_before_suspend="snd_hda_intel"*
to
*force_unload_modules_before_suspend=""*

and
sudo chmod -x /usr/lib/pm-utils/sleep.d/45sound

Then add following to /etc/pm/config.d/config
```

SUSPEND_MODULES="$SUSPEND_MODULES snd_hda_intel"
RESTORE_SOUND="yes"

```

Then suspend and resume.

---

### Post by Jws0001 on 2008-09-14
Wow... it restored from standby much quicker and absolutely no problems with the sound or the mixer applet.  I've been reading a decent amount though about people having problems with the sound not turning off when the machine is shutdown.  I believe I took care of that issue in another script... somewhere (so many to remember them all)... but will this have any effect on the standby process?  I've also  heard of people bleeding their batteries away because the sound doesn't get disabled during standby.

idk, I guess yes your solution worked but could you make me feel a little more comfortable about it :P

---

### Post by Jws0001 on 2008-09-14
Nvm.  Doesn't work.

After the first time it seemed to be just fine but after subsequent suspends the sound stopped working on certain programs.  Also when I plug in my headphones the sound comes out of both the earphones as well as the speakers.

Very buggy/unstable.

---

### Post by foobunt on 2008-09-17
Then I've no idea left. :sad:

You could try a "sudo /sbin/alsa reload" to see which process is preventing the modules form being unloaded. Probably the process is useless anyway and you can kill him before suspend.

---

