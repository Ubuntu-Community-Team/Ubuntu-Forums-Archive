---
title: "need to format /home when going from kubuntu to xubuntu?I"
date: 2009-05-22
forum: Installation &amp; Upgrades
---

### Post by helwitch on 2009-05-22
I currently have kubuntu 9.04 on my laptop. I want to switch to xubuntu. Do I need to format /home when I do this? I intend to install some kde using software after the switch, like kmymoney, so I figured that having the various kde directories still in place in /home won't be a problem. Will it?

---

### Post by tommcd on 2009-05-22
First off, why do you want to replace Kubuntu with Xubuntu?
If you are expecting a performance increase, I don't think you will get much of an increase in performance with Xubuntu compared to Kubuntu, especially if you are running KDE apps. If you are looking for faster performance, you might consider Debian with XFCE. See this review of both Debian and Xubuntu:
[http://distrowatch.com/weekly.php?issue=20090427#feature](http://distrowatch.com/weekly.php?issue=20090427#feature)
If you are just looking to replace KDE with XFCE, and faster performance is not your main concern, then I would just delete all the hidden config files and folders in /home. If you are doing a clean install then all those directories and files will be recreated anyway; and there will be no chance for confilcts.

EDIT: Just by way of comparison, on my Slackware system there is really no significant difference in performance between XFCE and KDE, especialy since I run KDE apps like K3B and Kaffeine on XFCE on Slackware. And Slackware is much faster than Ubuntu. XFCE may load a bit faster than KDE, and use less memory; but after you start running apps, especially KDE apps, there is really no difference.

---

### Post by helwitch on 2009-05-22
> **tommcd said:**
> First off, why do you want to replace Kubuntu with Xubuntu?
Because KDE4 sucks, and I'm tired of trying to work around the suck. I've got xubuntu on my netbook, and it's way more functional for me.
So, xubuntu will create any needed files&directories in /home, even if I don't format the partition where /home is? I'll delete all the hidden kde directories and files, but my concern is that xubuntu won't properly create directories&files in /home if /home isn't formatted when xubuntu is installed. I've got /home on a separate partition from /.
Edit-I do appreciate the advice on how to improve performance, but that's not really my goal. I like ubuntu well enough as an OS, I just am tired of the slow erosion of customizability&accessibility in KDE. XFCE seems far more configurable and accessible, which is my main concern for GUI.

---

### Post by tommcd on 2009-05-22
> **helwitch said:**
> 
So, xubuntu will create any needed files&directories in /home, even if I don't format the partition where /home is? 
Yes, a clean install will re-create all the config files you need. Just choose manual partitioning and mount your home partition as home. If you then install any KDE apps, then their config files will be created also. I think you will be fine.

I also don't like KDE 4. I have read that KDE 4.2 has finally got it right. I think KDE 4.2 will be included in Slackware 13.  I prefer the clean and simple interface of XFCE though. The only thing I really need KDE for is K3B. There is no question that K3B is the best CD / DVD burning app for linux.

---

### Post by snowpine on 2009-05-22
Xubuntu and Kubuntu are just Ubuntu with different desktop environments. You don't need to reinstall the entire system to replace KDE with Xfce.

Check out this tutorial; it will save you a lot of time: [http://www.psychocats.net/ubuntu/purexfce](http://www.psychocats.net/ubuntu/purexfce)

---

### Post by helwitch on 2009-05-22
> **snowpine said:**
> You don't need to reinstall the entire system to replace KDE with Xfce.
d'oh! I knew that, and completely wasn't thinking about it. I feel foolish now. Thanks for the reminder!

---

