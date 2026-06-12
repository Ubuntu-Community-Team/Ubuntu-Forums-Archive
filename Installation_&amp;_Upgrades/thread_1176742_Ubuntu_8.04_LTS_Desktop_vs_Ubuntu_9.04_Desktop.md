---
title: "Ubuntu 8.04 LTS Desktop vs Ubuntu 9.04 Desktop"
date: 2009-06-02
forum: Installation &amp; Upgrades
---

### Post by Spaceman9 on 2009-06-02
I'm confused about which to install. Ubuntu 8.04 LTS Desktop is supported until 2011 but Ubuntu 9.04 Desktop is only supported until 2010. If I install 8.04 LTS will I get everything from the new versions of Ubuntu or will I be stuck with just the stuff in 8.04 until 2011? How does this work?

 It would be great to not have to reinstall Ubuntu every six months but I've tried the upgrades using the package installer and it never seems as good as a fresh install. Thankx for any help.

---

### Post by argail1980 on 2009-06-02
well I usually stick with the most recent version, seeing how fast ubuntu has developed in the last few years. Most of the distro upgrades worked fine (except 710->8.04, that screwed up my system) so you should have a good backup. The recent update to jaunty worked like a charm.

If you install 8.04 there will be no major software upgrades, only security updates (i.e. 8.04 still has OpenOffice 2.4 and will keep it).

But I also see your point, that you don't want to upgrade every 6 months. BTW you can also skip every second version, the support runs a year I believe.

---

### Post by Spaceman9 on 2009-06-02
> **argail1980 said:**
> well I usually stick with the most recent version, seeing how fast ubuntu has developed in the last few years. Most of the distro upgrades worked fine (except 710->8.04, that screwed up my system) so you should have a good backup. The recent update to jaunty worked like a charm.

If you install 8.04 there will be no major software upgrades, only security updates (i.e. 8.04 still has OpenOffice 2.4 and will keep it).

But I also see your point, that you don't want to upgrade every 6 months. BTW you can also skip every second version, the support runs a year I believe.

Danke argail1980. I guess if the software isn't updated then there's no point in installing 8.04 LTS. I wonder if I could install the new versions of Ubuntu into 8.04 LTS using the upgrade thing?

---

### Post by arubislander on 2009-06-02
> **Spaceman9 said:**
> I wonder if I could install the new versions of Ubuntu into 8.04 LTS using the upgrade thing?

No, I don't think that is recommended. There isn't any simple way of doing that anyhow. If you upgrade 8.04 LTS you'll get 8.10. If you've already installed 9.04 and it works, your best bet is to stick to that. And as argail1980 said, you don't *have* to upgrade every 6 months...

---

### Post by argail1980 on 2009-06-02
If you use the update-manager, a button will appear when a new version is released, you just click and relax (well, I usually don't relax, till the new version finally boots).
You can also run ```
sudo do-release-update
``` in a terminal if you have update-manager-core installed.

This updates all the systems packages and rewrites the apt-sources (well, in reverse order..) Attention: third-party sources will be disabled, you can re-enable them later when you're sure they are meant for the correct release.

Also, you'll have to go from version to version, you cannot, i.e. upgrade from 8.04 to 9.04 directly. In this case I would recommend a fresh install. 
After Hardy, I decided to keep up with the new versions and I'm fine with that now.

---

### Post by Spaceman9 on 2009-06-02
> **arubislander said:**
> No, I don't think that is recommended. There isn't any simple way of doing that anyhow. If you upgrade 8.04 LTS you'll get 8.10. If you've already installed 9.04 and it works, your best bet is to stick to that. And as argail1980 said, you don't *have* to upgrade every 6 months...


Thankx arubislander. I guess I'll use 9.04 then...may be. I have 2 drives I can use for Linux. I could install 8.04 LTS on one and 9.04 on the other. But which drive would it be better to put 8.04 LTS on? May be I should use the first drive for 9.04. that way when I install 9.10 it's GRUB would over write the old GRUB on the MBR so may be I wouldn't have to do any editing of the menu.ls or whatever it is in the boot folder.

---

### Post by Spaceman9 on 2009-06-02
> **argail1980 said:**
> If you use the update-manager, a button will appear when a new version is released, you just click and relax (well, I usually don't relax, till the new version finally boots).
You can also run ```
sudo do-release-update
``` in a terminal if you have update-manager-core installed.

This updates all the systems packages and rewrites the apt-sources (well, in reverse order..) Attention: third-party sources will be disabled, you can re-enable them later when you're sure they are meant for the correct release.

Also, you'll have to go from version to version, you cannot, i.e. upgrade from 8.04 to 9.04 directly. In this case I would recommend a fresh install. 
After Hardy, I decided to keep up with the new versions and I'm fine with that now.


argail1980 I have 9.04 Xubuntu now but I'm D/Ling Ubuntu 8.04 LTS even as I type. May be I should do the 2 drive thing. May be with Ubuntu 9.04 on the first drive. I don't know.

---

### Post by arubislander on 2009-06-02
May I ask why it is you want to try 8.04 LTS (not that you owe me an explanation, mind you, I'm just curious)

---

### Post by Spaceman9 on 2009-06-02
> **arubislander said:**
> May I ask why it is you want to try 8.04 LTS (not that you owe me an explanation, mind you, I'm just curious)


I just think it would be nice to leave an instillation on my hard drive longer than 6 months. It seems like, over the last 2 years since I started using Linux, I've installed and reinstalled so many times I wonder why my hard drives haven't cought fire and burned up by now.

And now I'm sitting here thinking may be I should reinstall UbuntuStudio. See what I mean...lol

---

### Post by arubislander on 2009-06-07
Ok, I understand. But You know that no one is forcing you to upgrade/install every 6 months, right?

---

### Post by markbuntu on 2009-06-08
I am still using hardy 8.04 as my primary system. It is very stable now and does everything I need. Updates are down to a few per week. It is basically zero maintenance now and will be for a few more years but the first six months or so were not so easy with hardy.

I also have Debian, Mandriva, SUSE and Jaunty9.04 on this machine.....and may put Fedora 11 on it soon. They are my toys. Most of them I just try for a while and then forget about them and eventually replace them with something newer. New releases always have problems, sometimes small, sometimes big, but problems nonetheless.

Being on the bleeding edge is fun but not to be trusted for getting serious work done in a timely fashion. Unless you have a compelling need, hardware or software wise, it is better to stick to something that is stable and will be supported for a long time. I will probably start contemplating what to use for my new main install late next year. Hopefully the new Ubuntu LTS will be out and stabilized by then. 

just my 2 cents...

---

