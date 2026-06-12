---
title: "Ubuntuzilla and flash"
date: 2009-11-02
forum: Installation &amp; Upgrades
---

### Post by Samurijder on 2009-11-02
Hello Everybody,

About a 2 weeks ago I tried to upgrade firefox through ubuntuzilla, jaunty still had the 3.0 firefox. After ubuntuzilla installed the 3.5 version of firefox, flash was no longer working. After downgrading back to 3.0 and removing ubuntuzilla, the problem remained.
Synaptic told me flash was still installed.
My system is running on a 64-bit AMD turion CPU, 2 GB of RAM.

Can anyone please help me?

Thanks,

Martijn

---

### Post by masux594 on 2009-11-02
let's check what kind of flash plugin have u currently installed..go to about:plugins of your firefox.. So, what flash plugin have you?

Sysc, A

---

### Post by Samurijder on 2009-11-02
according to firefox, none..

---

### Post by masux594 on 2009-11-02
```
sudo apt-get install flashplugin-nonfree
```

This solve your problem?

Sysc, A

---

### Post by Samurijder on 2009-11-02
No, the latest version was already installed, as are the latest versions of flashplugin-installer, libsvwdec-0.8-0 and swfdec-gnome according to synaptic.

---

### Post by masux594 on 2009-11-02
is installed but as we seen, firefox does not have a flash plugin in the settings.. Try to remove flashplugin-installer, and the flashplugin-nonfree..

```
sudo apt-get remove flashplugin-installer flashplugin-nonfree
```
and then reinstall only the "nonfree" one
```
sudo apt-get install flashplugin-nonfree
```

Then?

Sysc, A

---

### Post by Samurijder on 2009-11-02
Unfortunately, no. About:plugins still claims nothing's installed and youtube either javascript is disabled or that I've got an old adobe flashplayer.

By the way, thank you very much for your help. I really apreciate it.

Martijn

---

### Post by masux594 on 2009-11-02
.. i'm sorry, but i'll never surrender so easy =)

Yes, youtube say's that when the browser were not able to manage flash .. So, the first command, does remove something or not?

Sysc, A

---

### Post by Samurijder on 2009-11-02
It certainly does. It removes flashplugin installer and the nonfree, and the second command reinstalls them. 
I've just checked my add-ons, but there's nothing like a java-blocker..
Previously downloaded .flv video's aren't a problem for totem, so flash appears to be in (some) working order, just not for firefox.

Martijn

---

### Post by masux594 on 2009-11-02
Looks very strange.. well, just recap.. When u installed "flashplugin-nonfree", firefox didn't have the plugin in the about:plugins page.. but is installed.. hmm.. .. a stupid question that i wouldn't ask.. have u completely close firefox and then reopen it? .. still nothing in about:plugins?

Sysc, A

---

### Post by Samurijder on 2009-11-02
Yes, I restarted firefox. I've even rebooted the entire system during the entire proces just to be sure (a bit overkill probably.. ;) )

---

### Post by masux594 on 2009-11-02
.. .. Hmm.. very strange.. ..Looks that firefox 3.5 doesen't set the plugin as your default flash plugin.. have u even installed the 3.0.x version of ff? both 3.5.x and the 3.0.x version?

Sysc, A

---

### Post by Samurijder on 2009-11-02
ff 3.0.x is not installed. ff 3.5.x is installed, including gnome-support
at [http://s606.photobucket.com/albums/tt142/samurijder/?action=view&current=firefoxinstalled.png](http://s606.photobucket.com/albums/tt142/samurijder/?action=view&current=firefoxinstalled.png) you can see what is installed concerning firefox

---

### Post by Samurijder on 2009-11-02
[this]("http://s606.photobucket.com/albums/tt142/samurijder/?action=view&current=firefoxinstalled.png") should show what I've got installed concerning ff

---

### Post by masux594 on 2009-11-02
totem.. Hmm.. If u try to remove totem-mozilla is there other packages that will be removed together?

Sysc, A

---

### Post by Samurijder on 2009-11-02
Couldn't this have something to do with 32bit flash on a 64 bit system? Pitty I can't find a 64 bit.
Do you mean try to remove totem and reinstall it?

---

### Post by masux594 on 2009-11-02
No, i've x64 system and flash 32bit..I mean, with 
```
sudo apt-get remove totem-mozilla
```
are there other packages that this command remove with the "totem-mozilla" one?

Sysc, A

---

### Post by Samurijder on 2009-11-02
Sorry, I misunderstood. Nope, nothing. I didn't use your command but synaptic instead, but I can't imagine how that would make a difference.

---

### Post by masux594 on 2009-11-02
totem-mozilla is even a flash plugin..
if removing totem-mozilla pakage does not remove other pakage, then u can remove it and re-install the flashplugin-nonfree that i said before.. have u understand now?

Sysc, A

---

### Post by Samurijder on 2009-11-02
I've removed totem-mozilla, removed the flashplugin and the nonfree, reinstalled the nonfree (and the plugin). Still no plugin. I've also reinstalled the totem-mozilla, but this had the same result (none whatso-ever).
I can see you've dug in, and I appreciate it.

Martijn

---

### Post by masux594 on 2009-11-02
well, at this point, what i've to say is that the problem is FF.. I've no idea why your FF does not work as well.. so, what i've to say is uninstall FF and the reinstall it with another method.. I've a x64 system, FF 3.5.4 and flash work perfectly.. 

Sysc, A

---

### Post by Samurijder on 2009-11-02
I've reinstalled firefox, but nothing has changed. I did notice however that 9.10 is supplied with ff 3.5.3, so perhaps I'll test it with 3.5.4. Even though upgrading ff started all this mayhem

Martijn

---

### Post by masux594 on 2009-11-02
As i seen with others users, looks like a Karmic problem.. All the user that don't succeed to install Flash plugin in firefox, has Karmic.. I have Jaunty and I don't know if I upgrade to karmic, so.. if i find some resolution of this stuff, i'll post to you!

However, i suppose that is not a 3.5.3 problem.. but some internal problems of karmic release i suppose.. I'sure that these problems is going to be resolved, until that, just wait.. 

P.s. If u want you can use the previous [maybe more stable] release Jaunty!

Sysc, A

---

### Post by nanotube on 2009-11-02
> **Samurijder said:**
> Hello Everybody,

About a 2 weeks ago I tried to upgrade firefox through ubuntuzilla, jaunty still had the 3.0 firefox. After ubuntuzilla installed the 3.5 version of firefox, flash was no longer working. After downgrading back to 3.0 and removing ubuntuzilla, the problem remained.
Synaptic told me flash was still installed.
My system is running on a 64-bit AMD turion CPU, 2 GB of RAM.

Can anyone please help me?

Thanks,

Martijn

see the ubuntuzilla faq for 64bit users to get your plugins working on the mozilla build of firefox (which is 32bit)

[http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Ubuntuzilla_FAQ](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Ubuntuzilla_FAQ)

---

### Post by masux594 on 2009-11-03
Another user "Solved this problem" installing Jaunty.. So, i think that is a Karmic problem.. ..

Sysc, A

---

### Post by Samurijder on 2009-11-03
> **nanotube said:**
> see the ubuntuzilla faq for 64bit users to get your plugins working on the mozilla build of firefox (which is 32bit)

[http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Ubuntuzilla_FAQ](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Ubuntuzilla_FAQ)

Thanks, that did the works. I've tried it before and it didn't work, but it did the trick this time.

Martijn

---

### Post by Samurijder on 2009-11-03
Masus594,

Thanks for all your effort, I appreciate it.

Martijn

---

### Post by nanotube on 2009-11-03
> **Samurijder said:**
> Thanks, that did the works. I've tried it before and it didn't work, but it did the trick this time.

Martijn

great! :)

---

