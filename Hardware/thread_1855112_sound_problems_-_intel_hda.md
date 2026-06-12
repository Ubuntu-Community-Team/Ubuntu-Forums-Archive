---
title: "sound problems - intel hda"
date: 2011-10-05
forum: Hardware
---

### Post by uzerVot on 2011-10-05
Hi there.

I have some problems with the sound driver, I can hear all the sounds through the headphones, but nothing on the speakers.
All the information about the system is here:

[http://www.alsa-project.org/db/?f=c392165d46850a80612f6801c50f48dee451d39b](http://www.alsa-project.org/db/?f=c392165d46850a80612f6801c50f48dee451d39b)

tested different things, from this forum too, nothing works. I think the driver is installed correctly, so why isnt it working?

thanks a lot!


Bye

---

### Post by gordintoronto on 2011-10-05
If you run Sound Preferences and click the Output tab, what "Connector" is used? Have you tried others?

It's always useful to provide a bit of description of your system: Laptop or desktop? Speakers built-in or connected front or back? Likewise earphones.

---

### Post by Toz on 2011-10-05
Have a look here: [http://ubuntuforums.org/showthread.php?p=7279149#post7279149]("http://ubuntuforums.org/showthread.php?p=7279149#post7279149")

---

### Post by uzerVot on 2011-10-06
> **gordintoronto said:**
> If you run Sound Preferences and click the Output tab, what "Connector" is used? Have you tried others?

It's always useful to provide a bit of description of your system: Laptop or desktop? Speakers built-in or connected front or back? Likewise earphones.
its a laptop with biult in speakers

connector is called "Analogue Output", yes I tryed the other one - "Analogue Earphones"

---

### Post by uzerVot on 2011-10-06
> **Toz said:**
> Have a look here: [http://ubuntuforums.org/showthread.php?p=7279149#post7279149](http://ubuntuforums.org/showthread.php?p=7279149#post7279149)


thanks, but not worked at all..
now have another output called "Analogue Speakers"

other idias?

---

### Post by Toz on 2011-10-06
Try adding:
```
options snd-hda-intel model=auto probe_mask=1
```
to the end of the **/etc/modprobe.d/alsa-base.conf** file instead. 

If you still have the **/etc/modprobe.d/hda_intel.conf** file, delete it.

Reboot.If still no sound, rerun and post updated alsa-script info.

---

### Post by uzerVot on 2011-10-06
> **Toz said:**
> Try adding:
```
options snd-hda-intel model=auto probe_mask=1
```to the end of the **/etc/modprobe.d/alsa-base.conf** file instead. 

If you still have the **/etc/modprobe.d/hda_intel.conf** file, delete it.

Reboot.If still no sound, rerun and post updated alsa-script info.


it did not worked
new file is located here:

[http://www.alsa-project.org/db/?f=3662c1aad18573142a7d7b8620ff943bf5da0d50](http://www.alsa-project.org/db/?f=3662c1aad18573142a7d7b8620ff943bf5da0d50)

thanks

---

### Post by Toz on 2011-10-06
Try going into your sound settings and see if there is a switch there to disable headphones and enable speakers ([http://ubuntuforums.org/showpost.php?p=7585682&postcount=5]("http://ubuntuforums.org/showpost.php?p=7585682&postcount=5")).

Alternatively, install **pavucontrol** and have a look at the options on the "Output Devices" tab.

---

### Post by uzerVot on 2011-10-06
> **Toz said:**
> Try going into your sound settings and see if there is a switch there to disable headphones and enable speakers ([http://ubuntuforums.org/showpost.php?p=7585682&postcount=5](http://ubuntuforums.org/showpost.php?p=7585682&postcount=5)).

Alternatively, install **pavucontrol** and have a look at the options on the "Output Devices" tab.

the program you mentioned shows nearly the same data like the ubuntu standard program.

I tried every option, no change..

---

### Post by Toz on 2011-10-06
The script looks fine. Does the following make sound?
```
sudo rmmod snd_hda_intel

```then
```
sudo modprobe snd_hda_intel
```

---

### Post by uzerVot on 2011-10-07
> **Toz said:**
> The script looks fine. Does the following make sound?
```
sudo rmmod snd_hda_intel

```then
```
sudo modprobe snd_hda_intel
```


blue@as:~$ sudo rmmod snd_hda_intel
ERROR: Module snd_hda_intel is in use

hmm..

---

### Post by Toz on 2011-10-07
Running out of ideas here....

Try this. Edit the file **/etc/rc.local** and _before_ the "exit 0" command, enter the following:
```
rmmod snd_hda_intel
modprobe snd_hda_intel
```

Reboot. Any luck?

---

### Post by uzerVot on 2011-10-07
> **Toz said:**
> Running out of ideas here....

Try this. Edit the file **/etc/rc.local** and _before_ the "exit 0" command, enter the following:
```
rmmod snd_hda_intel
modprobe snd_hda_intel
```Reboot. Any luck?


thanks dude, 
but still no change..

getting sick on it..

---

### Post by Toz on 2011-10-07
How about this post? Worth a try?
[http://ubuntuforums.org/showpost.php?p=9173650&postcount=7]("http://ubuntuforums.org/showpost.php?p=9173650&postcount=7")

---

### Post by uzerVot on 2011-10-07
> **Toz said:**
> How about this post? Worth a try?
[http://ubuntuforums.org/showpost.php?p=9173650&postcount=7](http://ubuntuforums.org/showpost.php?p=9173650&postcount=7)


no change at all..
still not having sound comming out the speakers.:-k

---

### Post by Toz on 2011-10-07
I'm afraid I don't know why your sound is not working. Have a look at: [https://wiki.ubuntu.com/DebuggingSoundProblems]("https://wiki.ubuntu.com/DebuggingSoundProblems"). Towards the end there is a section "Reporting Sound Bugs". I think you should create a bug report.

This piece of information from your /var/log/dmesg file may be of relevance and you should reference it in your report:
```
[   18.367951] hda_codec: ALC1200: SKU not ready 0x598301f0
```

---

