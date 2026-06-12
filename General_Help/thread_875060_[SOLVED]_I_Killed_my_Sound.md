---
title: "[SOLVED] I Killed my Sound"
date: 2008-07-30
forum: General Help
---

### Post by smith_fan on 2008-07-30
I am running Ubuntu 7.10 on a Toshiba laptop.  The sound stopped working a while back and, now the volume control up beside the date, has a red circle with a slash through it.  When I click the Preferences on it, I see the following error message:  “No volume control GStreamer plugins and/or devices found.”

I'm not sure what I did to mess things up, but right from the start I have had issues with the sound.  I had to do something with ALSA (I'm not sure what, though) before I ever had working sound on this thing. 

On the 'Devices' tab in the Sound Preferences window, clicking the 'Test' button for Sound Events with Sound Playback set either as AutoDetect or Advanced Linux Sound Architecture results in the following error message:  “audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open resource for writing.”

Would somebody please help me to fix whatever I ignorantly broke?

Thanks!,
~D~

---

### Post by dexter.deepak on 2008-07-30
keep this as a last option : reinstall alsa.
i am attaching the drivers.
give them executable permissions :
```
sudo chmod a+x alsa_*.sh
```
now run the first one :
```
sudo ./alsa_1.sh
```
reboot
then execute :
```
sudo ./alsa_2.sh
```
reboot and you are done.

---

### Post by eival on 2008-07-30
im not sure if you're having the same issue ive had but sometimes when i turn down/mute my sound, when i turn it back up and unmute it the sound will still be muted. but i figured out all i have to do is just double click the mute button below the 2nd volume bar(not the main) and it fixes it. i dont think its displayed by default, look in the properties. when i get home in about an hour ill find out the exact name an repost

---

### Post by smith_fan on 2008-07-30
darin@Belinda:~$ sudo chmod a+x alsa_*.sh
[sudo] password for darin:
chmod: cannot access `alsa_*.sh': No such file or directory
darin@Belinda:~$

---

### Post by smith_fan on 2008-07-30
> **eival said:**
> im not sure if you're having the same issue ive had but sometimes when i turn down/mute my sound, when i turn it back up and unmute it the sound will still be muted. but i figured out all i have to do is just double click the mute button below the 2nd volume bar(not the main) and it fixes it. i dont think its displayed by default, look in the properties. when i get home in about an hour ill find out the exact name an repost

Eival, when I click on 'Open Volume Control', I get the following:  "No volume control GStreamer plugins and/or devices found."

Kinda seems to me like the low-level code that manages the H/W got removed somehow.  But, in Synaptic, several ALSA-related packages are displayed as being installed...:confused:

---

### Post by dexter.deepak on 2008-07-31
> **smith_fan said:**
> darin@Belinda:~$ sudo chmod a+x alsa_*.sh
[sudo] password for darin:
chmod: cannot access `alsa_*.sh': No such file or directory
darin@Belinda:~$

this is really strange..
try again :
download the attached files to your ~/Desktop .
now,```
sudo bash
cd ~/Desktop
chmod a+x alsa_1.sh
chmod a+x alsa_2.sh
./alsa_1.sh
```
reboot and try :
```
cd ~/Desktop
sudo ./alsa_2.sh
```

---

### Post by smith_fan on 2008-07-31
We're slowly getting closer!  Unfortunately, we're not there, yet.  After renaming the files back to the plain default name and putting 'em on the Desktop (thanks for spellin' it out, BTW!), running your commands switches me to root.  Not knowing what to do then, I just run the same things over.  Here is what I've got:
"
darin@Belinda:~$ sudo bash
[sudo] password for darin:
root@Belinda:~# sudo bash
root@Belinda:~# cd ~/Desktop
root@Belinda:~/Desktop# chmod a+x alsa_1.sh
chmod: cannot access `alsa_1.sh': No such file or directory
root@Belinda:~/Desktop# chmod a+x alsa_2.sh
chmod: cannot access `alsa_2.sh': No such file or directory
root@Belinda:~/Desktop# ./alsa_1.sh
"

By “~/Desktop”, you just mean on the Desktop, right?  I forget what the tilda signifies, but the error message sure kind of indicates we might be having a file location misunderstanding...:-k

Thanks for the help, Dexter!:wink:

~D~

---

### Post by voteforpedro36 on 2008-07-31
Put a ./ before those alsa-1.sh and alsa-2.sh. In other words,:

```
chmod a+x ./alsa_1.sh
```

Or:
```
chmod a+x ~/Desktop/alsa_1.sh
```

Right now, when you type it without the *./*, it looks for that file in /home/youruser. With the *./*, it looks for it in the current directory (making it faster than typing ~/Desktop/file).

---

### Post by smith_fan on 2008-07-31
Pedro,

Thanks for the explanation!  Unfortunately, there's still a problem someplace...:
"
darin@Belinda:~$ chmod a+x ./alsa_1.sh
chmod: cannot access `./alsa_1.sh': No such file or directory
darin@Belinda:~$ chmod a+x ~/Desktop/alsa_1.sh
chmod: cannot access `/home/darin/Desktop/alsa_1.sh': No such file or directory
darin@Belinda:~$ 
"
I'm not seeing what it is, though.
:mad:

Anybody see the glitch?

Thanks!,
~D~

---

### Post by voteforpedro36 on 2008-07-31
> **smith_fan said:**
> Pedro,

Thanks for the explanation!  Unfortunately, there's still a problem someplace...:
"
darin@Belinda:~$ chmod a+x ./alsa_1.sh
chmod: cannot access `./alsa_1.sh': No such file or directory
darin@Belinda:~$ chmod a+x ~/Desktop/alsa_1.sh
chmod: cannot access `/home/darin/Desktop/alsa_1.sh': No such file or directory
darin@Belinda:~$ 
"
I'm not seeing what it is, though.
:mad:

Anybody see the glitch?

Thanks!,
~D~

Wait, so where are the files saved at?

---

### Post by smith_fan on 2008-07-31
They're right on the Desktop, AFAIK.

---

### Post by smith_fan on 2008-07-31
They were on the Desktop.

Somewhere along the way they had picked-up a period.  Once I'd renamed them from 'alsa_1..sh' and 'alsa_2..sh' back to 'alsa_1.sh' and 'alsa_2.sh', your commands worked perfectly.:)

When I rebooted, I had my sound back!:guitar:
:D

Thanks so much!,
~D~

---

