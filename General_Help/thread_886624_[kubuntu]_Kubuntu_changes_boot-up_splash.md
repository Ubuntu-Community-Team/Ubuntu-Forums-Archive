---
title: "/ [kubuntu] Kubuntu changes boot-up splash"
date: 2008-08-11
forum: General Help
---

### Post by PCessna on 2008-08-11
Hey all,

*Now I do dislike KDE, but it doesn't mean I don't like going on it every now and then, so today I install the Desktop manager. It's awesome how my files and stuff blend in well like I used Kubuntu. ANYWAYS*.

When I rebooted, I first saw the KDE splash while it shuts down you know it goes backwards of how much its done halting, and when I booted, I saw it again, I was like crap crap KDE WAS set at default.. and the login manger was xubuntu because I tried that, I went to synaptic, finished uninstalled xubuntu, changed login screen, my LAST PROBLEM IS, I want it back to Ubuntu, because Kubuntu gives me the chills, anyone know how to change the bootup spalsh from Kubuntu to Ubuntu again,

Thanks all
-PCessna

---

### Post by tuxxy on 2008-08-11
You could try

```
sudo dpkg-reconfigure gdm
```

Guide is available [here]("http://linuxfud.wordpress.com/2006/08/13/changing-from-ubuntu-to-kubuntu/")

---

### Post by tarps87 on 2008-08-11
You can also try:
```

sudo aptitude install usplash-theme-ubuntu

```
This will install the ubuntu boot screen and then:
```

sudo dpkg-reconfigure usplash

```
I hope this helps

---

### Post by PCessna on 2008-08-11
Bigger problem, no longer displays a splash, just the booting up text and shutting down. Holy crap.

Anyone know to DISPLAY a splash.

---

### Post by PCessna on 2008-08-11
> **PCessna said:**
> Bigger problem, no longer displays a splash, just the booting up text and shutting down. Holy crap.

Anyone know to DISPLAY a splash.

Anyone..please

---

### Post by sayakb on 2008-08-11
```
sudo apt-get install startupmanager
```
Then start it by System->Administration->Startup-Manager, click on Appearance tab and change the usplash theme.

---

### Post by lordadi on 2008-08-11
Hi,

Go and get Startup manager from the repos. Then Sytem > Admin > Startup Manager in Gnome (dont know how to do this in KDE).Then appearance tab in SUM (StartUpManager) and change your usplash theme.The default one is usplash-theme-ubuntu (clck on manage to add it, then go to wherever it is).

I have also attached the usplash theme for you. Unzip it and do the following
```
sudo cp <the unzipped *.so> /usr/lib/usplash/
```
Then in appearance, Usplash Theme, Manage Usplash theme go to the path /usr/lib/usplash/ and select usplash-theme-ubuntu.so

Cheers,


Lordadi.

A bit late!

---

### Post by PCessna on 2008-08-11
Now I've lost it. It won't work, Ubuntu can't read the one this person gave me so now I have NONE..  WHAT DO I DO?

PLEASE HELP ME. WHY WON'T IT WORK.

I don't get it omfg...

(WHAT DO I CONFIGURE IN THIS STUPID STARUP UTILITY)

---

### Post by PCessna on 2008-08-11
> **PCessna said:**
> Now I've lost it. It won't work, Ubuntu can't read the one this person gave me so now I have NONE..  WHAT DO I DO?

PLEASE HELP ME. WHY WON'T IT WORK.

I don't get it omfg...

(WHAT DO I CONFIGURE IN THIS STUPID STARUP UTILITY)

how much anyone wants to bet theyll be no more replys ;)

---

### Post by lordadi on 2008-08-11
Hi,

Once you download the file, decompress it (sorry about this but, right click and extract here) THEN do ```
sudo cp <the unzipped *.so> /usr/lib/usplash/
```

For example, you download to your desktop, then right click and select extract here. After that in a terminal ```
sudo cp /home/<your username>/Desktop/usplash-theme-ubuntu.so /usr/lib/usplash/
```

Then go to StartUpManager (System > Admin > StartUp Manager) then go to the appearance tab, and then go to Manage usplash themes. Then browse your way to /usr/lib/usplash/ and select usplash-theme-ubuntu.so and apply the change.

Sorry if this seems to be oversimplified and overexplained or if you feel i have insulted your intelligence, but i thought my previous post was clear as mud.

Cheers,


Lordadi.

---

### Post by lordadi on 2008-08-12
Hi,

Boot options tab:
Everything upto Default OS is your choice.
Display Res is again dependent on your system.
My color depth is set @ 24.
Show bootloader, Show Boot Splash are to be checked. The last one is your choice.

Appearance tab:
Bootloader menu colors are your choice.
Use bootloader themes is unchecked
Usplash themes is to be selected as usplash-theme-ubuntu

Security tab:
Dependent on you. Nothing checked for me

Advanced tab:
Dependent on you. I have 2 kernels and the first 2 under Misc. checked.


Hope this helps you,


Lordadi.

---

### Post by PCessna on 2008-08-12
> **lordadi said:**
> Hi,

Boot options tab:
Everything upto Default OS is your choice.
Display Res is again dependent on your system.
My color depth is set @ 24.
Show bootloader, Show Boot Splash are to be checked. The last one is your choice.

Appearance tab:
Bootloader menu colors are your choice.
Use bootloader themes is unchecked
Usplash themes is to be selected as usplash-theme-ubuntu

Security tab:
Dependent on you. Nothing checked for me

Advanced tab:
Dependent on you. I have 2 kernels and the first 2 under Misc. checked.


Hope this helps you,


Lordadi.
Nothing is working. WHY WON'T IT CHANGE. *sigh* I'm literally sick to my stomach now.. Can't eat for another half an hour D:
Edit: Ok, calmed down:
## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=E238AE9138AE63EF loop=/ubuntu/disks/root.disk ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
from grub loader, could this be BAD?

---

### Post by PCessna on 2008-08-12
> **PCessna said:**
> Nothing is working. WHY WON'T IT CHANGE. *sigh* I'm literally sick to my stomach now.. Can't eat for another half an hour D:
Edit: Ok, calmed down:
## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=E238AE9138AE63EF loop=/ubuntu/disks/root.disk ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
from grub loader, could this be BAD?

Anyone, Please?

-Boot splash will not show
-Settings are as the guy's above, expect resolution is 640x800 or whatever
-I don't know what to do
-I've tryed everything
Please help
bump

---

### Post by PCessna on 2008-08-12
> **PCessna said:**
> Anyone, Please?

-Boot splash will not show
-Settings are as the guy's above, expect resolution is 640x800 or whatever
-I don't know what to do
-I've tryed everything
Please help
bump
I guess theres nothing anyone can do *sigh*

---

### Post by lordadi on 2008-08-12
Did you try the stuff in post 3 above? It uninentionally worked for me.


Lordadi.

---

### Post by PCessna on 2008-08-13
> **lordadi said:**
> Did you try the stuff in post 3 above? It uninentionally worked for me.


Lordadi.

NOTHING works, I tried everything bro.

---

### Post by PCessna on 2008-08-14
> **PCessna said:**
> NOTHING works, I tried everything bro.

bump, please help, I can try to give as much info as possible.

---

