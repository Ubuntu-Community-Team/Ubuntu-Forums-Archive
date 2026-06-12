---
title: "Tried to install FF3.5 and messed everything up.."
date: 2009-07-17
forum: Installation &amp; Upgrades
---

### Post by running_rabbit07 on 2009-07-17
Can someone help me?

I just tried to install FF3.5 the way I found in another thread on my 8.04 machine and now I have no firefox at all, I tried using Synaptic Package Manager to reinstall 3.0 and it didn't work. I tried the command below it and it said the file wasn't there to remove.

I am using the LiveCD right now. I also restarted the PC to see if that would help. Now I have no tool bars. All I have is the desktop photo and the one file that was on the desktop.

These are the commands I ran,
cp -R ~/.mozilla ~/.mozilla.backup
sudo tar -jxvf firefox-*.tar.bz2 -C /opt
rm firefox-*.tar.bz2
sudo mv /opt/firefox/plugins /opt/firefox/plugins.backup
sudo ln -s /usr/lib/xulrunner-addons/plugins /opt/firefox/plugins
sudo ln -s /opt/firefox/firefox /usr/local/bin/firefoxand 

this is the one I just tried to use to fix,

sudo rm /usr/local/bin/firefox && sudo rm -r /opt/firefox



Can anyone help me get back up and running without having to reformat?

Thanx.

---

### Post by running_rabbit07 on 2009-07-17
Wow, I just realized how fast FF3.5 works on Windows. anyway if it comes down to it, should I reinstall Ubuntu 8.04 without telling it to reformat the /home will it not wipe out the /home drive?

---

### Post by M1A1_Gunner_120mm on 2009-07-18
> **running_rabbit07 said:**
> Can someone help me?

I just tried to install FF3.5 the way I found in another thread on my 8.04 machine and now I have no firefox at all, I tried using Synaptic Package Manager to reinstall 3.0 and it didn't work. I tried the command below it and it said the file wasn't there to remove.

I am using the LiveCD right now. I also restarted the PC to see if that would help. Now I have no tool bars. All I have is the desktop photo and the one file that was on the desktop.

These are the commands I ran,
cp -R ~/.mozilla ~/.mozilla.backup
sudo tar -jxvf firefox-*.tar.bz2 -C /opt
rm firefox-*.tar.bz2
sudo mv /opt/firefox/plugins /opt/firefox/plugins.backup
sudo ln -s /usr/lib/xulrunner-addons/plugins /opt/firefox/plugins
sudo ln -s /opt/firefox/firefox /usr/local/bin/firefoxand 

this is the one I just tried to use to fix,

sudo rm /usr/local/bin/firefox && sudo rm -r /opt/firefox



Can anyone help me get back up and running without having to reformat?

Thanx.

You should get that fixed.

---

### Post by running_rabbit07 on 2009-07-18
> **M1A1_Gunner_120mm said:**
> You should get that fixed.

Yeah, thanks.

LovingLinux tried to help me via another thread but I just couldn't get any of the keyboard commands to open anything so I had to reinstall Ubuntu.

What do you call a tanker without a tank?

---

### Post by Greenwidth on 2009-07-18
> **running_rabbit07 said:**
> 
What do you call a tanker without a tank?

er?

---

### Post by running_rabbit07 on 2009-07-18
Tanker
Without A
Tank

mispaced A on purpose

---

### Post by spiralx on 2009-07-18
I just did that upgrade.  It's called Shiretoko Web Browser (no, I don't know why either!).

You can pick it up via Synaptic, and it installs as a separate browser to FF3, so you have to go through the slight faff of removing the FF launch panel icon, and replacing it with the Shiretoko icon.

Otherwise, it works just fine - imports everything as you would expect.

---

### Post by running_rabbit07 on 2009-07-18
> **spiralx said:**
> I just did that upgrade.  It's called Shiretoko Web Browser (no, I don't know why either!).

You can pick it up via Synaptic, and it installs as a separate browser to FF3, so you have to go through the slight faff of removing the FF launch panel icon, and replacing it with the Shiretoko icon.

Otherwise, it works just fine - imports everything as you would expect.

I was going for the FF branded version, they are both the same though from what I have been reading. Shireteko isn't in the 8.04 Synaptic. I am sure I could get it easily but I am gonna wait until the branded version is in there. I decided that if it ain't broken then I am not going to fix it.

---

