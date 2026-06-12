---
title: "Need to recover GDM"
date: 2008-10-27
forum: General Help
---

### Post by jbalcaen on 2008-10-27
Hello Everyone,

I was following this tutorial [http://nerdica.com/?p=30](http://nerdica.com/?p=30) when I unknowingly deleted the link to gdm in my init.d folder using:

```
sudo update-rc.d gdm remove
```

This has caused my system to become command line only on startup.

I tried undoing it by using 

```
sudo update-rc.d gdm defaults
```

Then I tried deleting the file and running the above command again but that was a bad idea because now I receive 
```
sudo update-rc.d gdm defaults
update-rc.d: /etc/init.d/gdm: file does not exist

```

I figured out that using the following command restores the gui.
```
gdm
```


I tried using synaptic to recover gdm, I marked it for reinstallation but my system still boots into command line mode.

Anyone know how I can restore the gdm file that was in /etc/init.d/

Thanks in advance.

---

### Post by Eilin Chang on 2008-10-27
Hi,

Have you managed to install gdm again? have you tried to login into command line mode and run the command **startx**?
If that makes come up your gui, check your /etc/inittab file to see what is your default runlevel set up to.
I'm not an expert at this nor anything like that, I just happen to have been playing with that recently, if it doesn't work I'm not sure I can be of any more help.

Hope you can solve it!

---

