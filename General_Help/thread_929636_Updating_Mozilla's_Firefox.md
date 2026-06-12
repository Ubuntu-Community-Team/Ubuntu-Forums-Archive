---
title: "Updating Mozilla's Firefox"
date: 2008-09-25
forum: General Help
---

### Post by Nabanna on 2008-09-25
Hello,

I have installed Mozilla Firefox in Ubuntu 8.04, i want to update it to its latest version, but **'Check for updates'** is grayed out so i cannot click on it and update.
Please suggest how to update Mozilla Firefox ..???

---

### Post by prshah on 2008-09-25
> **Nabanna said:**
> 
I have installed Mozilla Firefox in Ubuntu 8.04, i want to update it to its latest version, but **'Check for updates'** is grayed out so i cannot click on it and update.

You don't really need to do this; ubuntu will tell you and offer to upgrade firefox when there is an pdated version available in the repositories.

However, if you want to go ahead anyway (not recommended), close all instances of firefox, press Alt+F2 and give the command ```
gksudo firefox
``` The "Check for updates" option will now be available to you.

You do this at your own risk!

---

### Post by Nabanna on 2008-09-25
> **prshah said:**
> You don't really need to do this; ubuntu will tell you and offer to upgrade firefox when there is an pdated version available in the repositories.

However, if you want to go ahead anyway (not recommended), close all instances of firefox, press Alt+F2 and give the command ```
gksudo firefox
``` The "Check for updates" option will now be available to you.

You do this at your own risk!

Thanks....
but i didnt got any notifications for the update..
(i came to know about the update when i used Windows and saw that it was released on Sept-23)

Also, will this command open Ubuntu's Firefox or Mozilla Firefox.
(i am using Mozilla Firefox)


Regards..

---

### Post by aysiu on 2008-09-25
I don't think the *gksudo firefox* and check for updates will work if you're using the repos version of Firefox.

---

### Post by prshah on 2008-09-25
> **Nabanna said:**
> 
Also, will this command open Ubuntu's Firefox or Mozilla Firefox.
(i am using Mozilla Firefox)

I don't understand. Even ubuntu's firefox will open as "Mozilla Firefox"; do you feel you have some other firefox? My firefox Help-About says:> Firefox 3.0.2
Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.2) Gecko/2008092313 Ubuntu/8.04 (hardy) Firefox/3.0.2 Does yours read different?

> **aysiu said:**
> I don't think the *gksudo firefox* and check for updates will work if you're using the repos version of Firefox.

It ungreys the option to check for updates.. I don't know beyond that.

---

### Post by mikewhatever on 2008-09-25
> **Nabanna said:**
> Hello,

I have installed Mozilla Firefox in Ubuntu 8.04, i want to update it to its latest version, but **'Check for updates'** is grayed out so i cannot click on it and update.
Please suggest how to update Mozilla Firefox ..???

Did you know Firefox comes pre-installed with 8.04? Can you elaborate a bit on the way you've installed it?

> **prshah said:**
> 
It ungreys the option to check for updates.. I don't know beyond that.

If you download a binary from Mozilla and install it manually, the option to update may get active with gksudo, however, there is no such thing as auto updating as in Windows. At the most, firefox will open the download page, and you'd have to download the new package and reinstall manually again.

---

### Post by Nabanna on 2008-09-25
(sorry, i didnt intended to disagree or argue.., please forgive if someone felt so)

I have installed **firefox-3.0.1.tar.bz2**  downloaded from *[http://www.mozilla.com/en-US/firefox/all.html](http://www.mozilla.com/en-US/firefox/all.html)* 

and i asked so after reading the article and warning in para 2 at *[https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion)*,

also when i try to open it using terminal it shows eula as it showed when i first installed it.

kindly help, i want to update as soon as possible..

---

### Post by pluckypigeon on 2008-09-25
If you want the newest Firefox then add this to the repo list

```


deb http://ppa.launchpad.net/fta/ubuntu/ intrepid main multiverse restricted universe
deb-src http://ppa.launchpad.net/fta/ubuntu/ intrepid main multiverse restricted universe



```

---

### Post by aysiu on 2008-09-25
> **pluckypigeon said:**
> If you want the newest Firefox then add this to the repo list

```


deb http://ppa.launchpad.net/fta/ubuntu/ intrepid main multiverse restricted universe
deb-src http://ppa.launchpad.net/fta/ubuntu/ intrepid main multiverse restricted universe



```
I think that's a really bad idea.

Mixing and matching repository versions can lead to breakage.

Intrepid repositories should not be on a Hardy installation.

---

### Post by pluckypigeon on 2008-09-25
> **aysiu said:**
> I think that's a really bad idea.

Mixing and matching repository versions can lead to breakage.

Intrepid repositories should not be on a Hardy installation.

Thanks for your feedback

You could listen to him... He is a Forum Admin after all.. and yes it is possible that it could break...like any other 3rd party repo. Maybe I should have mentioned that before. 

I've personally been using this repo for ages now without problems.

---

### Post by SuperSonic4 on 2008-09-25
> **prshah said:**
> I don't understand. Even ubuntu's firefox will open as "Mozilla Firefox"; do you feel you have some other firefox? My firefox Help-About says: Does yours read different?



It ungreys the option to check for updates.. I don't know beyond that.

That's because 3.0.2 is the latest and therefore most up to date version of firefox.

---

### Post by pluckypigeon on 2008-09-25
> **SuperSonic4 said:**
> That's because 3.0.2 is the latest and therefore most up to date version of firefox.

3.0.3 is actually the latest. I'm using it.

---

### Post by SuperSonic4 on 2008-09-25
It is? Then disregard my last post :)

So it is, I updated it. What does ```
sudo apt-get update
``` do?

---

### Post by bingoUV on 2008-09-25
> **Nabanna said:**
> (sorry, i didnt intended to disagree or argue.., please forgive if someone felt so)

I have installed **firefox-3.0.1.tar.bz2**  downloaded from *[http://www.mozilla.com/en-US/firefox/all.html](http://www.mozilla.com/en-US/firefox/all.html)* 

and i asked so after reading the article and warning in para 2 at *[https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion)*,

also when i try to open it using terminal it shows eula as it showed when i first installed it.

kindly help, i want to update as soon as possible..

I read the guide about installing Mozilla's build of firefox in Ubuntu. It mentions unpacking the tar.bz2 in /opt, using sudo. Thus, the directory that will contain the mozilla binary (opt/firefox/) is owned by root and the regular user does not have write permissions in this directory.

Firefox disables the "Check for updates" button when the user running firefox does not have write permissions on the directory containing firefox binary.

You have 2 options.
1. Make yourself the owner of firefox directory, and run firefox. Now the update button will be enabled. Update, and again make root the owner of firefox.
```

chown -R <user>:<user> /opt/firefox

```

after updating, 
```

chown -R <root>:<root> /opt/firefox

```


2. Run /opt/firefox/firefox as root, update
```

sudo /opt/firefox/firefox

```

---

### Post by pluckypigeon on 2008-09-25
> **SuperSonic4 said:**
> It is? Then disregard my last post :)

So it is, I updated it. What does ```
sudo apt-get update
``` do?

It updates the repositories to the new upgrades. If you want to upgrade you have to do that first and then ```
sudo apt-get upgrade
```

---

### Post by bingoUV on 2008-09-25
> **pluckypigeon said:**
> It updates the repositories to the new upgrades. If you want to upgrade you have to do that first and then ```
sudo apt-get upgrade
```

apt-getting won't help SuperSonic4 as the guide he has followed instructed him to dpkg-divert away all updates to firefox. So, only /opt/firefox/firefox will be run no matter how much you apt-get.

---

### Post by pluckypigeon on 2008-09-25
> **bingoUV said:**
> apt-getting won't help SuperSonic4 as the guide he has followed instructed him to dpkg-divert away all updates to firefox. So, only /opt/firefox/firefox will be run no matter how much you apt-get.

He only asked what it does. So I told him. What's wrong with that?:confused:

---

### Post by bingoUV on 2008-09-25
> **pluckypigeon said:**
> He only asked what it does. So I told him. What's wrong with that?:confused:

Nothing wrong. Sorry if it felt like that. Only there were too many posts here about repos, apt-get etc which are not useful for the original poster.

---

### Post by pluckypigeon on 2008-09-25
> **bingoUV said:**
> Nothing wrong. Sorry if it felt like that. Only there were too many posts here about repos, apt-get etc which are not useful for the original poster.

Sorry, I should have read the thread a bit more thoroughly before answering rashly like that :(

---

### Post by oldsoundguy on 2008-09-25
FF update will update completely if you are using Hardy and upwards as you installed 3.x when you installed the system and the updates will be in your repositories.

The "gksudo firefox &" command is (or should be) used ONLY if you installed the Ubuntuzilla version from the site (Source Forge) on an OLDER version of Ubuntu.  I did the do on three Gutsy machines yesterday without a problem.

As has been pointed out, going outside the repositories is a chancy thing and should be done only after some serious research and sometimes soul searching.  
Having said that, Source Forge is really a reliable source OUTSIDE of those repositories. (but keep your desktop backed up at least!)

---

### Post by Nabanna on 2008-09-25
> **bingoUV said:**
> Run /opt/firefox/firefox as root, update
```

sudo /opt/firefox/firefox

```

Thank you, this worked and updated to latest version3.0.2 (~700kb update)

---

