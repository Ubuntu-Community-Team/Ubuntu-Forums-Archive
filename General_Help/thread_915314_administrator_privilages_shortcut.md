---
title: "administrator privilages shortcut"
date: 2008-09-09
forum: General Help
---

### Post by Adnanius on 2008-09-09
hi,
every time I want to start googleearth, I should use the command line to have administrator privilages, otherwise googleearth dosen't work normally.
so, how can I make a shortcut with administraror's privilages enabled for this application? and maybe would there be a way to add googleearth as an *open* application so it dosen't ask for the administrator's password ?
Adnan

---

### Post by Vivaldi Gloria on 2008-09-09
How did you install GE?

---

### Post by zoomy942 on 2008-09-09
yeah google earth is really tricky to install on ubuntu.

how did you install it?

---

### Post by Vivaldi Gloria on 2008-09-09
I'm going to sleep so let me tell you how to install GE the right way, which doesn't require to be run as admin.

Google Earth is available in the medibuntu repos:

[http://www.medibuntu.org/](http://www.medibuntu.org/)

Follow the howto there to add medibuntu to your repo list. If you have ubuntu 8.04 hardy heron then these are the commands:

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

Now you can install GE using synaptic:

system menu > admin > synaptic

---

### Post by Adnanius on 2008-09-09
Actually, i have it already installed, 
I just need a shortcut with which I can open directly the application.
A way to give the ordinary user the 'permission' to open ge

and about how i installed, I got the googleearthLinux.bin on google's web and sh googleearthlinux.bin
that's what I remember.

---

### Post by devosion on 2008-09-09
Thanks Vivaldi, i've also been looking for the correct way to install Google Earth.

---

### Post by Vivaldi Gloria on 2008-09-09
> **Adnanius said:**
> Actually, i have it already installed, 
I just need a shortcut with which I can open directly the application.
A way to give the ordinary user the 'permission' to open ge

and about how i installed, I got the googleearthLinux.bin on google's web and sh googleearthlinux.bin
that's what I remember.

Right click an empty area in a panel and choose add to panel then choose custom launcher. Use the command "gksudo googleearth" for it. 

Then you can drag it to desktop if you want.

@devosion - You're welcome.

Good Night boys and girls.

---

### Post by Adnanius on 2008-09-09
okay thanks, and good night!

---

### Post by Vivaldi Gloria on 2008-09-09
> **Adnanius said:**
> okay thanks, and good night!

Wait, I realized that that wouldn't work. Wait.

---

### Post by Adnanius on 2008-09-09
it's gksu googleearth and not gksudo
it works

---

### Post by Vivaldi Gloria on 2008-09-09
> **Adnanius said:**
> it's gksu googleearth and not gksudo
it works

I hope it does. But a password is good for 10 minutes. Are you sure that you waited long enough to try it?

If it still doesn't work then you have two options:

1) Uninstall & reinstall using the above method. 

2) Find where GE is installed. Probably in one of

```
/usr/bin/googleearth
/usr/sbin/googleearth
/root/.googleearth/googleearth
/home/username/.googleearth/googleearth
```

To see the hiddenfiles press ctrl+H in nautilus file browser.

Then in a terminal change its ownership to you:

```
 sudo chown -R username:username /usr/bin/googleearth
```

where username is your username and change /usr/bin/googleearth to its install path.

Or make it executable by everyone by giving the command

```
 sudo chmod -R 755 /usr/bin/googleearth
```

See

```
man chown
man chmod
```

for more info on these commands.

--------------------

Now really going to sleep. I'll check this thread again tomorrow.

---

