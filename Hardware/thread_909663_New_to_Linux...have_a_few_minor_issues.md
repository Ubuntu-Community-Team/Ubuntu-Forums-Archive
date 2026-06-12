---
title: "New to Linux...have a few minor issues"
date: 2008-09-03
forum: Hardware
---

### Post by themrfreeze on 2008-09-03
Hi all.

After being a Mac user since 1992, I've decided to give Linux a try.  Apple's getting a little too "Big Brother" for my tastes. :(

To that end, I've installed the latest version of Xubuntu on a Thinkpad R32.  Overall, everything works pretty well and I'm very happy that I've made the switch.  However, I'm experiencing a few minor issues, and I'm hoping that perhaps somebody could help with them.  I've searched the forums for answers, but haven't found anything relevant.

First, sound works fine when you boot the computer, but if you suspend or hibernate the computer, sound stops working and won't work again until I reboot.  I'm guessing that reloading the sound driver when the computer wakes up will fix it, but I have no idea how to set that up.  Xubuntu lists the sound as being "Intel 82801CA-1CH3", if that helps.

Second, when I tell the computer to shutdown, Linux closes, the screen goes black, but the computer itself doesn't shut down...the cooling fans come on and the computer just sits there. I have to hold the power button down for 5-10 seconds to force it to shut off.  Anything I can do to fix this?

TIA for any help you can provide!

---

### Post by tommcd on 2008-09-03
For the shutdown problem perhaps you could have a look at this to see if it pertains to you and if it helps:
[http://sadsoftware.blogspot.com/2008/03/linux-on-ibm-thinkpad-r32-shutdown.html](http://sadsoftware.blogspot.com/2008/03/linux-on-ibm-thinkpad-r32-shutdown.html)
Try usinf "sudo pccardctl eject" prior to shutdown as it says in the article.

Also try the solution in posts #6 and 7 in this thread:
[http://ubuntuforums.org/showthread.php?t=396418](http://ubuntuforums.org/showthread.php?t=396418)
Also try turning "wake on LAN" options off in your laptop's BIOS. See post #6 in this thread.
[http://ubuntuforums.org/showthread.php?t=785693&highlight=Thinkpad+R32+shutdown](http://ubuntuforums.org/showthread.php?t=785693&highlight=Thinkpad+R32+shutdown)
Also try from terminal "sudo shutdown -h now" See if you can shutdown with that.
Hope some of this helps.
And welcome to the Ubuntu forums!!

---

### Post by themrfreeze on 2008-09-04
Thanks for the reply (and the welcome)!  Turning off "Wake on LAN" fixed the shutdown problem.  Now if I can figure out the audio issue, I'd have this system running 100%.

---

### Post by themrfreeze on 2008-09-08
I've made a little more headway with the audio problem.  Maybe with this info, somebody more familiar with the innards of Linux than me (which is pretty much anybody reading this) could help me fix this?

What I found is that after I wake the computer up from suspend mode, audio does not work.  However, if go into the mixer and change the PCM level, then adjust the master volume, sound will start working again.  It doesn't work if I just adjust master volume, PCM has to be done first.

In xfce4-mixer, I have the Intel audio device selected, with "Master,0" set for the "Wannabe Master".

I was able to figure out that '/etc/init.d/alsa-utils' is what starts and stops the audio, that it's called by '/etc/acpi/resume.d/67-sound.sh', and utilizes a file called '/var/lib/alsa/asound.state'.  I'm happy to tweak the PCM/Master volume levels upon restart to correct this, but I have no idea how one would do this.  Can one of these files be modified to do this, or is there a way to add a script (perhaps to the end of the resume process) to do this automatically?

---

