---
title: "Intrepid Upgrade Hangs on Obsolete Software"
date: 2008-10-30
forum: General Help
---

### Post by Unanimated on 2008-10-30
This might happen on all upgrades, I don't know. This is my first distribution upgrade. The Distribution Upgrade window is open and everything, but it's hanging on its search for obsolete software. It's been doing this (hanging) for about 2 hours now. I don't know if it should be that long. The bar hasn't moved at all, and the terminal window has been showing this for 2 hours:

```
ldconfig deferred processing now taking place
```

Among other things related to the new Intrepid kernel. Is this supposed to happen?

---

### Post by emoric on 2008-10-30
Wow, same here!

[IMG]http://i33.tinypic.com/2qwzgb4.png[/IMG]


I just posted a thread about it as well. :/

---

### Post by Unanimated on 2008-10-30
Yeah, whatever. I'll just restart the computer - it's the next step in the upgrade, and this step is almost done. After 2 hours, it would have found some obsolete software, wouldn't it? Yes.

---

### Post by Sef on 2008-10-30
> Yeah, whatever. I'll just restart the computer - it's the next step in the upgrade, and this step is almost done. After 2 hours, it would have found some obsolete software, wouldn't it? Yes.   	

It should not take that long.  If you click on terminal what does it show?   Sometimes restarting the computer can help, but at other times, you have to reinstall the Ubuntu via a clean install.

---

### Post by emoric on 2008-10-30
> **Unanimated said:**
> Yeah, whatever. I'll just restart the computer - it's the next step in the upgrade, and this step is almost done. After 2 hours, it would have found some obsolete software, wouldn't it? Yes.

Please, I would love to hear how it goes. I have restarted, but I have not tried the upgrade again. All I see on the forums is upgrade problems. :lol:

Maybe I will wait a few days ;/

And Sef, thank you for the heads up ;]

---

### Post by Unanimated on 2008-10-30
Yeah.. Restarting didn't help. Intrepid is bootable and working, but the update manager is the problem. It claims that I can install 747 updates, but I can't install them for 2 reasons:
1. Only a limited few are checked, claiming that I must do a partial upgrade to continue. Clicking Partial Upgrade takes me back to Distribution Upgrade, which claims that it can't do anything because it can't "upgrade" to Hardy.
2. Hitting Close on the Partial Upgrade window closes that window, but I can't check any other updates. Hitting Install Updates tells me to fix the broken packages first. Yay.

What do I do? Is there a way to fix this WITHOUT doing a clean install?

---

### Post by spiderbatdad on 2008-10-30
sounds like:```
sudo dpkg --configure -a
```time. Then run the update manager. But servers are likely to be heavily loaded right now so, maybe not the best time to run the update.

---

### Post by Unanimated on 2008-10-30
I don't know what that was supposed to do, but it didn't help. Running it in the terminal didn't produce anything, and the update manager gave me the same results both times.

---

### Post by Unanimated on 2008-10-30
I'm starting to consider downloading the Intrepid ISO and just doing a clean reinstall, after backing up meh home folder.

---

### Post by wisd0m on 2008-10-30
mine was hung on "...obsolete..." as well.

in the terminal it said:

```
Setting up linux-libc-dev (2.6.27-7.15) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place

```

I rebooted after an hour, did restore, apt-get autoremove and fix xorg. i booted and it seems to work. in sys-monitor it says 8.10.

should i try to re-install? am i done?

I am very new to this, I only switched over for day-to-day work a week ago, so some of the terms above may be wrong.

---

### Post by Wozbuntu on 2008-10-31
I too had this issue of being frozen on searching for obsolete software for 2 hours, and rebooted.



My sys-monitor says Release 8.10, but my update manager wants to 'upgrade' from 'intrepid' to 'hardy'...



Anyone got any clever ideas???

Edit:
Thanks for the idea Philop. The "safe-upgrade" worked.

First time round it didn't work. Started the upgrade before I went out last night, but it only updated about half of the packages (probably due to the servers being swamped by people trying to get Intrepid). After reboot the GUI would start to load (could see by wallpaper), but would go no further. Simple CTRL-ALT-F1, and retrying the "safe-upgrade", and it all worked perfectly.

Thanks again Philop :-)

---

### Post by Philop on 2008-10-31
I had the same problem, the update manager locked up on removing obsolete software. After rebooting the update manager told me it couldn't upgrade to Hardy (...) using
> $ cat /etc/lsb-release
showed
> DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.10
DISTRIB_CODENAME=intrepid
DISTRIB_DESCRIPTION=”Ubuntu 8.10&#8243;

So I am following the instructions [on this page]("http://chrisjohnston.org/2008/upgrading-from-ubuntu-804-hardy-heron-to-810-intrepid-ibex"). The "safe-upgrade" is updating more than 750 packages right now. ...

---

### Post by pbm on 2008-10-31
Exact same problem for me upgrading Kubuntu from 8.04.1. The upgrade stalls on ldconfig deferred processing. this is on a 3 month old MSI Wind clone.

---

### Post by Unanimated on 2008-10-31
Yeah.. What I did is I had all my music backed up onto my MP3 player, then I backed everything up into a bz2 file following a certain howto, and now I'm just going to do a clean reinstall. I'm downloading the Intrepid ISO now, and it's incredibly fast - there's at least 100 seeds at all times.

---

### Post by jikuty on 2008-10-31
I'm having the same problem... hanging on "Searching for obsolete software" with the ldconfig notice in the terminal.

Any way I can fix this without having to do a fresh install? Kind of ruins the whole ease-of-use Ubuntu advantage if I have to format in order to upgrade.

---

### Post by emptiness on 2008-10-31
same problem here...
hanging on removing obselete software,I really don't have time at the moment to do a fresh install.

Using a macbook Core2duo gen 3,1 with ubuntu as my only os.

If I do fresh install wont I lose all of my custom settings and apps?


EDIT: The safe-upgrade option appears to be working...  so far.
Thanks for the link Philop

---

### Post by emoric on 2008-10-31
I was able to avoid the clean install. I went into recovery mode and I want to say the I did dpkg? Sounds about right. Took about an hour, I'm not sure what did it. Seems like it did some updating and then rebooted. I was able to log into Intrepid.

So, lesson learned. I may end up staying with the long term releases. :lol:

---

### Post by emptiness on 2008-10-31
Okay,

after doing the "safe-upgrade" the update manager prompted me to do a partial upgrade and am trying that now.We'll see.
Anyway I downloaded the install disc torrents just in case,thank god for torrents!!
seed,seed,seed!!!

Also after doing the "safe-upgrade" this is what I got from $ cat /etc/lsb-release 

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.04
DISTRIB_CODENAME=hardy
DISTRIB_DESCRIPTION="Ubuntu 8.04.1"

Weird...

---

### Post by wisd0m on 2008-10-31
> **emptiness said:**
> 
Also after doing the "safe-upgrade" this is what I got from $ cat /etc/lsb-release 

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.04
DISTRIB_CODENAME=hardy
DISTRIB_DESCRIPTION="Ubuntu 8.04.1"

Weird...

how to you do a "safe-upgrade"? i can no longer launch *Software Sources* or Install from *add/remove*. 

help...:guitar:

---

### Post by notmatt on 2008-11-01
wisd0m, 

Try

sudo aptitupe update
sudo aptitude safe-upgrade

As it says here:

[http://chrisjohnston.org/2008/upgrading-from-ubuntu-804-hardy-heron-to-810-intrepid-ibex](http://chrisjohnston.org/2008/upgrading-from-ubuntu-804-hardy-heron-to-810-intrepid-ibex)

HTH

Matt

---

### Post by ea1475 on 2008-11-01
> **wisd0m said:**
> how to you do a "safe-upgrade"? i can no longer launch *Software Sources* or Install from *add/remove*. 

help...:guitar:

I had the SAME problem with the inability to launch Software Sources. And when launching the update manager, it says that I need to do a partial upgrade, or something. I think I've got some of the packages, but now compiz isn't working. I'm so frustrated.

---

### Post by simbahome on 2008-11-02
I also got problems on upgrade as described above, my  

```
cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.10
DISTRIB_CODENAME=intrepid
DISTRIB_DESCRIPTION="Ubuntu 8.10"

```

My Software Sources disappeared, while my Update Manager wants to do a partial update to Hardy from Intrepid and then crashes.

Anyone got any bright ideas?:confused:

Thanks

---

### Post by kanenas on 2008-11-02
I have the same problem with you guys

ldconfig deferred processing now taking place
(after 2 hours I kill the update manager)

Now the software sources program does not work
and according to cat /etc/lsb-release
it seems that I have 8.10?

I tried everything dpkg reconfigure, apt install -f
do-upgrade, sudo updatemanager -c -d etc
but I can not update/upgrade because ubuntu thinks
that I already have.

So I tried the alternative cdromupgrade approach

I downloaded the alternative 8.10 cd I burned it and 
mount it, then from terminal I went to the
media/cdrom directory and typed

sudo cdromupgrade

In the question do you want to use the Internet bla bla bla 
I answered "no" and in less than 20 minutes everything seems
to be perfect

If you tried everything else and it fails do the cdromupgrade

---

### Post by wisd0m on 2008-11-03
> **ea1475 said:**
> I had the SAME problem with the inability to launch Software Sources. And when launching the update manager, it says that I need to do a partial upgrade, or something. I think I've got some of the packages, but now compiz isn't working. I'm so frustrated.

I just backed up all files (except Firefox bookmarks...damn) and reinstalled 8.10 AMD64. Its works fine now!

I had the advantage that I had only been using Ubuntu full-time for a week, not a lot of clutter to backup. 

I really suggest giving up and reinstalling, surrender to the tech.

---

### Post by barney_1 on 2008-11-04
This is a bunch of bull-corn.  I spent 2 days waiting for the updates to download and now i might have to do it again?

Did anyone put in a bug report yet?

---

