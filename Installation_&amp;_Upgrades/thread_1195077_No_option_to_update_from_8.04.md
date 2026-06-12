---
title: "No option to update from 8.04"
date: 2009-06-23
forum: Installation &amp; Upgrades
---

### Post by afflusso on 2009-06-23
I have ubuntu 8.04 installed, which I think came as an upgrade through the update manager from feisty. But now the update manager doesn't give me any option to update past 8.04. 

Shouldn't there be a message when there's a distribution upgrade available? :confused:

---

### Post by raymondh on 2009-06-23
> **afflusso said:**
> I have ubuntu 8.04 installed, which I think came as an upgrade through the update manager from feisty. But now the update manager doesn't give me any option to update past 8.04. 

Shouldn't there be a message when there's a distribution upgrade available? :confused:

software sources (system > admin > update tab > release upgrade > choose NORMAL > close)

Then
```

sudo apt-get update
sudo apt-get upgrade
```

For reference

[https://help.ubuntu.com/community/IntrepidUpgrades](https://help.ubuntu.com/community/IntrepidUpgrades)

This will update you to 8.10.

To update to 9.04 from thereon,

-  Make sure you are updated first in 8.10
-  When ready, software sources again
-  update and upgrade

For reference

[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)


You can also do

sudo apt-get dist-upgrade

---

### Post by raymondh on 2009-06-23
PS ... If willing,  download, burn and try the liveCD of your choice first and see how it reacts to your system specs.  The liveCD is usually a good indicator of things to come.

Good luck and Happy Ubuntu-ing.

---

### Post by afflusso on 2009-06-23
Thanks.
When I try update, it says a few things and then 

dpkg --configure -a

but when I try that it gets a ton of errors, and then

!queuelen failed
Aborted.

Also Firefox suddenly won't work on that box now so that's why I couldn't copy the whole thing. If you know what my problem might be, that would greatly help. If you need me to copy everything, I can if it helps.

---

### Post by raymondh on 2009-06-23
```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```

Did not work?   Can you post the errors?

-  Make sure you are only using one manager.  Either terminal or synaptic or add/remove.
-  Are all the repos checked?  System > admin > software sources > ubuntu (except CD rom) & 3rd party & updates 

You could also force an install

```
sudo apt-get -f install
```

Let's see the errors.

---

### Post by afflusso on 2009-06-23
The force install didn't work.

I copied the output to a text doc, but I can't save it anywhere, and Firefox, pidgin, and mounting a USB drive don't work, so I can't copy that to here unless I retype all of it. I think the main problem is that it's saying read-only in a few places (which is why I couldn't even save the txt doc). How could my drive have become read-only?

*When I load ubuntu I did skip a fsck or something, but from what I remember if I don't skip it ubuntu will never load.

---

### Post by raymondh on 2009-06-23
> **afflusso said:**
> The force install didn't work.

I copied the output to a text doc, but I can't save it anywhere, and Firefox, pidgin, and mounting a USB drive don't work, so I can't copy that to here unless I retype all of it. I think the main problem is that it's saying read-only in a few places (which is why I couldn't even save the txt doc). How could my drive have become read-only?

*When I load ubuntu I did skip a fsck or something, but from what I remember if I don't skip it ubuntu will never load.

how about a screenshot of the terminal output showing the errors?  make sure you expand the terminal?

Also, are you still in 8.04 or in 8.10 now?  Either version, make sure your sources.lst only reflect the version you are using. .... i.e, if you are using 8.10, make sure your sources.lst  has 'intrepid' and not 'hardy'.

EDIT : I am going to log out for work ... will check back in 5 hrs.  Good luck.

---

### Post by afflusso on 2009-06-23
> **raymondhenson said:**
> how about a screenshot of the terminal output showing the errors?  make sure you expand the terminal?

Also, are you still in 8.04 or in 8.10 now?  Either version, make sure your sources.lst only reflect the version you are using. .... i.e, if you are using 8.10, make sure your sources.lst  has 'intrepid' and not 'hardy'.

EDIT : I am going to log out for work ... will check back in 5 hrs.  Good luck.

Since I have no way of transferring data, I can't provide a screenshot. Thanks for your help, but I  will be away for a while, when I get back to this I'll revive the thread.

---

### Post by mocoloco on 2009-06-23
It's recommended you upgrade through the update manager rather than command line and changing your sources. Make sure it's set to offer you all releases, not just LTS (Long Term Support) releases.
System -> Administration -> Software Sources.  On the "Updates" tab, the bottom option should show "Normal releases" to be able to upgrade past 8.04.

---

### Post by raymondh on 2009-06-23
Hi Affluso,

See this link and browse to the end for a TIP with regard to your dpkg problem after upgrading to 8.10

[https://help.ubuntu.com/community/HardyUpgrades#Upgrading%20Using%20the%20Alternate%20CD/DVD](https://help.ubuntu.com/community/HardyUpgrades#Upgrading%20Using%20the%20Alternate%20CD/DVD)

---

