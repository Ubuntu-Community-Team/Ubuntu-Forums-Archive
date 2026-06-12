---
title: "Problem upgrading Xubuntu 7.04 to 7.10"
date: 2009-07-16
forum: Installation &amp; Upgrades
---

### Post by Thaddeus11 on 2009-07-16
Hi all,

A friend asked me to load Xubuntu on his system as a dual boot.  Installed Xubuntu 7.04 as thats what I had burned on a CD.  I've completed the 7.04 install.  I'm looking to upgrade to the latest and am having a problem.

I've updated sources.list as reported in this posting ([http://ubuntuforums.org/showthread.php?p=6319924](http://ubuntuforums.org/showthread.php?p=6319924)) and was able to update.

However, when I tried to upgrade to Xubuntu 7.10 (clicking on the upgrade button in Update Manager), it's giving me an error reporting that it can't find the release notes.

"New distribution release 7.10 is available "

Error message "Could not find the release notes"

Tried searching for that message but it's got so many generic words, I'm getting nothing useful.  Does anyone know or have suggestions on how to resolve that so I can get this machine upgraded?

Thanks,
Thaddeus

---

### Post by snowpine on 2009-07-16
I recommend a fresh install of the current version, 9.04 Jaunty Jackalope.

7.04 and 7.10 have both reached "end of life" and are no longer supported.

---

### Post by drs305 on 2009-07-16
I agree with snowpine. Trying to upgrade an EOL release wouldn't really be worth the effort if you can get the .iso of a current release.

If you *really* want to go the route you are asking about, here is the link for End of Life (EOL) upgrades:
[EOLUpgrades]("https://help.ubuntu.com/community/EOLUpgrades")

---

### Post by Thaddeus11 on 2009-07-16
Thanks for the link drs305.  That'll gives me the info I am looking for to go in the direction I want to go.  I greatly appreciate you giving information on resolving the issue based on the route I chose.

Snowpine, I understand that these releases are no longer supported which is why I am looking to upgrade to newer releases.  Isn't 'Reinstall the OS' answers one of the reasons why people bash Windows so bad?  Besides, if someone told me to blindly reinstall to 9.04 on my laptop over 8.10 and I lost Compiz and such due to my onboard ATI chips, I'd be pretty ripped.

I would have loved to install the latest but the burn of iso I had was bad (think my burners going as I've been getting lot of bad burns).  The 7.04 disk was good and available.  I wasn't expecting that 'no longer supported' means we'll break/change/remove the upgrade process, too.  Doesn't doing that require the user to need support that Canonical no longer wants to give...

I've been touting Linux for years now and finally got a friends curiosity up enough to want me to install on his PC.  It was rather embarassing after telling him about how easy it is to do updates with Ubuntu and have Update Manager tank twice (once due to repository locations being changed) and again when trying to upgrade to a newer release.

I appreciate that caninical doesn't want to spend time on older releases but why did they have to break the upgrade process?  I wouldn't have needed assistance if they didn't.

Sorry for the rant.  I've been lurking on the Forums for a long time now and have been trying to show people the benefits of Linux and the great support in the forums.  But that gets so underminded by all of the flippant responses....

---

### Post by snowpine on 2009-07-16
Hi Thaddeus, I hear your rant... I do not personally agree with Canonical's decision to support each Ubuntu release for only 18 months, but it is what it is. (My ideal distro would be "rolling release" like Arch or Debian Sid, meaning you install once and get constant updates, rather than a new release every 6 or 12 months.) 

Just for the record, even if you had asked "how do I upgrade from 8.10 to 9.04?" I would still recommend a fresh install. I have spent too much time on these forums to have total faith in the Ubuntu release-upgrade process. Users who upgrade vs. reinstall seem to experience a disproportionate share of the problems.

Also understand that to get to the current release, you would have to sequentially update 7.04->7.10->8.04->8.10->9.04, which I simply can't recommend for sanity's sake.

ps Ubuntu does a "long term support" release every 2 years, with 3 years of support (instead of 18 months). Currently it is 8.04 Hardy Heron; next one comes out April 2010. Maybe a good choice for those users sick of the 6 month cycle. :)

(edit) And I apologize for being so brief in my original post. I am sure if I'd taken the extra minute to explain my reasons, it wouldn't seem flippant, cool? ;)

---

### Post by presence1960 on 2009-07-16
> **snowpine said:**
> Hi Thaddeus, I hear your rant... I do not personally agree with Canonical's decision to support each Ubuntu release for only 18 months, but it is what it is. (My ideal distro would be "rolling release" like Arch or Debian Sid, meaning you install once and get constant updates, rather than a new release every 6 or 12 months.) 

Just for the record, even if you had asked "how do I upgrade from 8.10 to 9.04?" I would still recommend a fresh install. I have spent too much time on these forums to have total faith in the Ubuntu release-upgrade process. Users who upgrade vs. reinstall seem to experience a disproportionate share of the problems.

Also understand that to get to the current release, you would have to sequentially update 7.04->7.10->8.04->8.10->9.04, which I simply can't recommend for sanity's sake.

ps Ubuntu does a "long term support" release every 2 years, with 3 years of support (instead of 18 months). Currently it is 8.04 Hardy Heron; next one comes out April 2010. Maybe a good choice for those users sick of the 6 month cycle. :)

(edit) And I apologize for being so brief in my original post. I am sure if I'd taken the extra minute to explain my reasons, it wouldn't seem flippant, cool? ;)

you are right on the mark about the upgrade process. if one peruses back thru this forum there is a remarkedly big proportion of upgrades that have gone amuck. If one has a separate home doing a clean install is a breeze. I have gotten away from a separate home partition myself. I have an ext 3 partition for data and I back up my home folder so I have all the config files if need be. When I do a clean install I just copy them over to the home folder and all my settings are back the way they were prior.

---

