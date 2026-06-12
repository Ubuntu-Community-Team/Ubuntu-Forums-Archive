---
title: "Issues with upgrade, Under new kernel, Nvidia crashes"
date: 2009-10-31
forum: Hardware
---

### Post by WarholsGhost on 2009-10-31
Hello dear ubuntu community,

so i was really excited to upgrade but i'm facing a really major issue right now and i'm hoping people can help me out.

I was running xubuntu 9.04 on my desktop computer, everything worked great. I tried to upgrade using update-manager but when it got to the point to download new packages, it failed. I blame this on the load of how many people were stressing the ubuntu servers. 

So i decided to do the more awesome thing and download the .torrent and upgrade using the cd. I downloaded and installed it but i made the mistake of using a ubuntu alternate cd (as opposed to xubuntu). that made things a bit funky. i was able to log into the computer via "recovery mode" in the new kernel but when i try to continue normal boot i get this:

* nvidia (180.44)
    Fail!

when i try to boot in normal mode, in the new kernel, the screen flickers a lot and the login dialog doesn't show up.

so i was able to boot into the computer with a gui via the old kernel so once i did that i got the right xubuntu cd and ran the update script again. 

the point i'm at now is that i still can't log in using the new kernel with a gui, only command line. I can log in using the old kernel but only with gnome not xfce.

i'm pretty sure my problem is with my nvidia driver, as that is the only thing that fails on start-up. If you think this is the problem, please include details on how to change the driver via command line.  

Any help is appreciated!

---

### Post by darco on 2009-10-31
there seems to be a few work arounds for this issue...search the forums and I am sure you will find a fix...


darco

---

### Post by Claus7 on 2009-10-31
Hello,

from what you are describing, I can understand that the driver is the problem. What you can do is to go to the nvidia web site, download the driver of your card and then install it via command line. 

Also does this command work for you?
sudo nvidia-xconfig

In addition I would try to uninstall any packages (from synaptic) having to do with nvidia and install them again, via command line. Yet, I have seen that the nvidia drivers (from web site) are doing the trick.

Regards!

---

### Post by WarholsGhost on 2009-11-01
so i'v gotten a bit farther. I ran "sudo apt-get upgrade" which took about 8 hours to install and setup a bunch of packages. 

then i installed the new driver, and now i can log in to gnome no problem, but xfce is still giving me problems. i want to run xfce as my WM, how can i get xfce working again?

---

### Post by Claus7 on 2009-11-01
Hello,

is it possible to do such a thing since you have gnome installed? I think that you can use only one of them, yet I might be wrong.

What do you mean that it gives you problems?

Regards!

---

