---
title: "Howto:  Workaround - sound after suspend - snd_intel8x0"
date: 2007-04-27
forum: Hardware &amp; Laptops
---

### Post by mia1dolfan on 2007-04-27
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/21574](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/21574) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				This was tested on Ubuntu Feisty using the 2.6.20-15-generic kernel.  These scripts run before and after the system suspends, removing the ALSA driver and inserting the OSS driver, and vise-versa when the system resumes.  This issue affects a wide range of laptops using the intel8x0 chipset.  I personally use a Compaq nc6230.

The scripts I started with have been taken from Mandriva's suspend-script rpm package and have been heavily modified.  Besides the Alsa / OSS module swap, the script kills any applications using the sound device before suspend, and attempts to restore the killed application after resume.

Unfortunately Ubuntu/Gnome users will be greeted with a "Volume Control" has quit unexpectedly dialog box after suspend.  Select the "reload" and the mixer will be replaced in the panel, a minor inconvenience.  I was unable to find a way to gracefully terminate the Gnome volume control (mixer) and reinstall it from the command line.  It must be unloaded to able to remove the ALSA modules.  KDE users won't have this problem as the script will replace the volume control application after resume.

**1.**  Download the two attachments below and place *87-kill.sound.sh* in */etc/acpi/suspend.d* and *66-resume-sound.sh* in */etc/acpi/resume.d*

**2.**  Run the following commands to set the proper file attributes.
```

sudo -v
sudo chown root.root /etc/acpi/suspend.d/87-kill-sound.sh
sudo chown root.root /etc/acpi/resume.d/66-resume-sound.sh
sudo chmod 755 /etc/acpi/suspend.d/87-kill-sound.sh
sudo chmod 755 /etc/acpi/resume.d/66-resume-sound.sh
```

**3.**  Test the suspend function, see if it works!


**More Information**

You might be wondering why I insert the OSS driver before suspend, the reason is simple, if I don't, and I only remove the ALSA driver and re-insert them after suspend the issue persists, weird huh?!

Now you might be wondering why I don't simply use the OSS driver and dump the ALSA driver, that's what I tried first, and I encountered a few problems.  The show stopper was the fact that Adobe Flash Player 9 for Linux only supports the ALSA sound system (bye-bye youtube).

---

### Post by maicua on 2007-04-29
smt doesnt work here ...
it didnt do the work for my laptop presario 2825EA :(

---

### Post by mia1dolfan on 2007-04-29
> **maicua said:**
> smt doesnt work here ...
it didnt do the work for my laptop presario 2825EA :(

Attach the file soundinfo.txt located on your desktop after running the code below.

```

sudo -v
uname -a >~/Desktop/soundinfo.txt
cat /etc/issue >>~/Desktop/soundinfo.txt
echo "************* Start lspci output" >>~/Desktop/soundinfo.txt
lspci >>~/Desktop/soundinfo.txt
echo "************* Start lsmod output" >>~/Desktop/soundinfo.txt
lsmod >>~/Desktop/soundinfo.txt
echo "************ Start kill script" >>~/Desktop/soundinfo.txt
sudo /etc/acpi/suspend.d/87-kill-sound.sh >>~/Desktop/soundinfo.txt 2>&1
echo "************* Start lsmod output" >>~/Desktop/soundinfo.txt
lsmod >>~/Desktop/soundinfo.txt
echo "************* Start resume script" >>~/Desktop/soundinfo.txt
sudo /etc/acpi/resume.d/66-resume-sound.sh >>~/Desktop/soundinfo.txt 2>&1
echo "************* Start lsmod output" >>~/Desktop/soundinfo.txt
lsmod >>~/Desktop/soundinfo.txt
echo "************* Start dmesg output" >>~/Desktop/soundinfo.txt
dmesg | tail -n 1 | cut -b 2-4 | xargs -i grep \\['{}' /var/log/messages >>~/Desktop/soundinfo.txt

# End
```

Attach the file located in your desktop called soundinfo.txt

---

### Post by maicua on 2007-04-29
thx for your rapid answer
here is the result ...

---

### Post by mia1dolfan on 2007-04-29
Can you run the commands to generate the output again?  I had a few syntax errors that produced an incorrect output.

---

### Post by maicua on 2007-04-30
the output file...

---

### Post by mia1dolfan on 2007-04-30
> **maicua said:**
> the output file...

I reviewed the output, and the script ran as it was suppose to.

My audio system
*Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)*

Your audio system
*Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)*

On your system there was a error reported when loading the OSS module
[I]ac97_codec: AC97 Audio codec, id: ADS99 (Unknown)
 i810_audio: AC'97 codec 0 Unable to map surround DAC's (or DAC's not present), total channels = 2[/I]

I googled around but couldn't find anything definite.  This may be a long shot, but could you flash your system's bios to the latest revision to see if that helps?

---

### Post by jabuntu on 2007-05-03
It was the solution to the resume-sound-problems on my IBM T41 laptop. 

Thanks!

---

### Post by kingjere on 2007-05-09
This along with adding my sound module to the /etc/default/acpi-support file under the remove and reload section fixed the sound issue on my IBM A21m, but Kmix doesn't reload after a suspend. This is, however,  minor as far as I'm concerned. b

---

### Post by tp21 on 2007-05-19
hi, 
i am having the same problem on my thinkpad T 21.
before using this workaround i am wondering if i should put the scripts in /etc/acpi/suspend.d or resume.d, because i start the kernel with acpi=off, and working with apm.
should i put the scripts in apm suspend.d and resume.d?
thanks

---

### Post by Josh Kurtz on 2007-05-24
No luck here.  I do, however, get sound out of my earphones after suspend-resume, just not from my laptop's speakers.

---

### Post by borris.morris on 2007-06-04
mine now works, i just have to manually run, "sudo modprobe snd_cs46xx" and then it works. so i made a quick launcher. is there any way to have it do this for me? other than that it works PERFECT on a thinkpad 600x. i have been looking for this for SO long you wouldnt believe. THANK YOU!!!!!

---

