---
title: "Beeeeeeeeeeeeeeeeeeeeeep !"
date: 2009-12-28
forum: Hardware
---

### Post by red33m on 2009-12-28
Hello everyone,

I have a Lenovo n500 laptop and every time I plug in/out the charger adapter..it makes a really loud BEEP noise.Can I disable it because it really is annoying?

P.S, Better late than ever Happy Christmas !

Thank you,

Red33m

---

### Post by zero-n on 2009-12-28
Try this :

- Go to System >> Preferences >> Sound

- Select System Beep tab.

- Un-check **[COLOR="Red"]Enable system beep[/COLOR]**.

---

### Post by red33m on 2009-12-28
I run on Kubuntu mate.... ;)

---

### Post by zero-n on 2009-12-28
Ok try this :

```
sudo echo "blacklist pcspkr" >> /etc/modprobe.d/blacklist
```

then restart.

---

### Post by red33m on 2009-12-28
it wrote me this..:

red33m@red33m:~$ sudo echo "blacklist pcspkr" >> /etc/modprobe.d/blacklist
bash: /etc/modprobe.d/blacklist: Permission denied
red33m@red33m:~$

what do I do?

---

### Post by rCXer on 2009-12-28
Try opening (or creating if it doesn't exist) "/etc/modprobe.d/blacklist" and add "blacklist pcspkr" to the file.

I have a T43p. When I did this awhile back, the beep on switching from battery to ac power was not disabled.  I think it's hardwired into IBM/Lenovo computers.

---

### Post by red33m on 2009-12-28
I googled it and Windows users are able to turn it off...

..You think that in (K)ubuntu is impossible...?

---

### Post by zero-n on 2009-12-28
I am not so familiar with KDE.

we can try to edit the same file from the GUI this time

1- open Konsole.

2- Run a text-editor as root : (Kate or KEdit)

```
gksudo kate
```

3- Edit **[COLOR="Red"]/etc/modprobe.d/blacklist[/COLOR]**

4- Add this line to the eof:
```
# Stop beeping !
blacklist pcspkr
```

i hope this will work with you

---

### Post by red33m on 2009-12-28
wow..too much info at once...I did the first two...I opened Kate as root..but then how/where do I do the next two commands ..?
 :)

---

### Post by zero-n on 2009-12-28
The next 2 steps are not command.

Open the file **[COLOR="Red"]blacklist[/COLOR]** which is locate in **[COLOR="red"]/etc/modprobe.d/[/COLOR]** using kate as root

at the end of file paste this :

```
# Stop beeping !
blacklist pcspkr
```

Save the file.

Restart.

---

### Post by red33m on 2009-12-28
Is the file blacklist supposed to be blank?

---

### Post by zero-n on 2009-12-28
Sorry the file name is **[COLOR="Red"]blacklist.conf[/COLOR]** not **blacklist**

---

### Post by red33m on 2009-12-28
nope...didn't work..still beeeping!

---

### Post by zero-n on 2009-12-28
After some digging if found this:

```
sudo modprobe -r pcspkr
```

---

### Post by Ayuthia on 2009-12-28
Have you tried going into System Settings->Notifications->System Bell and turning it off?  You might also check in Notifications->System Notifications and under the Event Source select Power Devil.  In there you can change the AC adaptor options so that it will not play a sound.

Hope that helps.

---

### Post by red33m on 2009-12-28
I hope it was that easy..you see when I plug in the AC adapter it makes two sounds...a nice one from the KDE and a stupid ugly beeeeep that breaks my nerves every time...has  to be the internal speaker

---

### Post by red33m on 2009-12-28
no it didn't work ...also it wrote this and I hope it doesn't get me into trouble in the future..:

red33m@red33m:~$ sudo modprobe -r pcspkr
[sudo] password for red33m:
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
red33m@red33m:~$

if you have any other ideas please tell me...I am going to sleep though because it is almost 3:00am here and I have to study tomorrow..thanks for all the help..!

---

### Post by juancarlospaco on 2009-12-28
Please use DESCRIPTIVE titles...

---

### Post by red33m on 2009-12-28
I'll give it a shot next time!

---

### Post by Ayuthia on 2009-12-28
Here is what I found:
[http://www.techsupportforum.com/hardware-support/laptop-support/335705-solved-disabling-beeping-sound-when-connecting-power-cord-into-laptop.html](http://www.techsupportforum.com/hardware-support/laptop-support/335705-solved-disabling-beeping-sound-when-connecting-power-cord-into-laptop.html)

It looks like there is a speaker option available.  I am thinking that in Kubuntu, you might need to right-click on the speaker icon in the system tray and select "Show Mixer Window".  You should get a list of speaker sound controls.  If you don't, you should be able to enable a few more through the Settings->Configure Channels on the menu bar.  There will most likely be something for PC Speaker or beep.  You should be able to mute it.

EDIT:  I just noticed that the answer there was for Vista, but hopefully the option will be there for you in the speaker settings in Kubuntu.

---

### Post by red33m on 2009-12-28
it is a brilliant idea but sadly there is not an option for the internal speaker...neither I can enable it..

---

