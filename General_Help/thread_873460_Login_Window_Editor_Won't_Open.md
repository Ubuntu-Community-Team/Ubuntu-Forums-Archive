---
title: "Login Window Editor Won't Open"
date: 2008-07-29
forum: General Help
---

### Post by Unanimated on 2008-07-29
Hi,
I downloaded the Black Mesa theme for the login screen from gnome-themes or whatever it's called, and I tried to open up Login Window from System->Administration, and it asks for my password. I put it in, then the actual window opens for about a second and then closes again. I restarted my computer, and my sound wasn't working for some reason, so I changed the output from ALSA to Multichannel and now it works. I'm just really wondering why the Login Window editor won't open.

---

### Post by YaroMan86 on 2008-07-29
Sometimes, especially when run for the very first time, it takes a while for the editor to open. Wait a while.

---

### Post by Unanimated on 2008-07-29
I've run it before, but my problem is that it shows the actual editor screen for about a second then closes again.

---

### Post by Unanimated on 2008-07-29
bump

---

### Post by Unanimated on 2008-07-29
bump

---

### Post by biasedopiniondrummer on 2008-07-29
i'm having the exact same issue. any word yet?

---

### Post by linnuxnub on 2008-07-29
> **biasedopiniondrummer said:**
> i'm having the exact same issue. any word yet?

Me too.

---

### Post by raab on 2008-07-29
Have you tried running it from a terminal window to see if it produces any errors?

---

### Post by Unanimated on 2008-07-29
What would I (we) have to put in?

---

### Post by Unanimated on 2008-07-29
Ok nevermind--I tried to open it using gksudo gdmsetup, and the same thing happened. No errors showed. I also tried using sudo gdmsetup, and I also tried su - [password] gdmsetup. Absolutely nothing happened. Except, when I tried to open it using su -, it returned this:
(gdmsetup:6191): Gtk-WARNING **: cannot open display:

---

### Post by Unanimated on 2008-07-30
bump..

---

### Post by Unanimated on 2008-07-30
bump...

---

### Post by raab on 2008-07-31
you're using gnome correct?

been googling and the only solution that I've seen seems to be reconfiguring xserver-xorg

> Save your actual xorg.conf and redo xorg configuration, from terminal:
cd /etc/X11
sudo cp xorg.conf xorg.conf.bak
sudo dpkg-reconfigure xserver-xorg
sudo reboot

---

### Post by Unanimated on 2008-07-31
Yes.

---

### Post by Unanimated on 2008-07-31
OH MY GOD MY RESOLUTION IS EXTREMELY MESSED UP
I had it on 1280x1024 and now it's stuck on 640x480. I updated the drivers with EnvyNG and I restarted it. Nothing is working. It keeps saying something about low graphics mode, not being able to detect my display, and every time I start it, I have to choose my screen and driver, which it completely ignores once it actually starts the OS.

---

### Post by Unanimated on 2008-07-31
**And it still won't open.**

---

### Post by Unanimated on 2008-07-31
Okay, now the login screen resolution is messed up. It's too big for my monitor, so I need the editor.. which of course won't open.

---

### Post by Unanimated on 2008-07-31
bump

---

### Post by Unanimated on 2008-07-31
bump

---

### Post by Unanimated on 2008-07-31
Bump

---

### Post by Unanimated on 2008-07-31
Wait, I tried running it through sudo gdmsetup again and it returned and said Segmentation fault.

---

### Post by Unanimated on 2008-07-31
Ok, I tried that sequence again, and my resolution didn't completely mess up, but it didn't solve the problem either.

---

### Post by Unanimated on 2008-08-01
bump

---

### Post by Unanimated on 2008-08-01
bump :frown:

---

### Post by Unanimated on 2008-08-02
bump

---

### Post by lori on 2008-08-09
> **Unanimated said:**
> Hi,

I tried to open up Login Window from System->Administration, and it asks for my password. I put it in, then the actual window opens for about a second and then closes again. 

Same thing happening here. I get "Segmentation Fault".
No-one can help? :(

---

### Post by lori on 2008-08-09
My problem has been resolved with RomeReactor's suggestion which can be found [here]("http://ubuntuforums.org/showpost.php?p=5433920&postcount=8").

---

### Post by Unanimated on 2008-08-09
No, that didn't work.

---

### Post by jerome1232 on 2008-08-09
I had this happen to me a while back, at the time I was using nvidia's drivers (from their site), recompiling the driver fixed the issue for me. I've also seen in another thread (will look for it in a minute) [http://ubuntuforums.org/showthread.php?t=841477](http://ubuntuforums.org/showthread.php?t=841477)  that reinstalling video drivers fixed it for another person.

good luck let me know if it helps

---

### Post by Unanimated on 2008-08-09
That didn't work, either.

---

### Post by Unanimated on 2008-08-10
Wait, I nevermind that-for the other people having problems, try RomeReactor's answer, then the answer below that. You will probably have to restart a few times, but now mine is just randomly working fine. Also, if you need to shut down the X server, write down the name of the driver, type sudo /etc/init.d/gdm stop, hit ctrl+alt+F1, then go through the process of installing the driver by typing...
cd ~/Desktop (if the driver is on the desktop)
chmod +x NAME_OF_DRIVER
sudo ./NAME_OF_DRIVER

I ask you to write down the name because it's usually long and drawn out.
Thanks to everyone who helped me(us)!

---

