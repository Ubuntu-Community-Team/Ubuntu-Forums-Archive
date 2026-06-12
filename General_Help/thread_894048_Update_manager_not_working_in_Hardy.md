---
title: "Update manager not working in Hardy"
date: 2008-08-18
forum: General Help
---

### Post by Andybr2000 on 2008-08-18
Update manager not working in Hardy
I had a problem with amsn and I follow the steps below to fix it, but now do not get the notification to update. I just have the notification to update amsn. 1 update to install.

To enable the proposed archive for hardy add the following line to /etc/apt/sources.list:
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-proposed restricted main multiverse universe
or go to System -> Administration -> Software sources and tick the hardy-proposed box under the updates tab.
close amsn window
Now open a shell and type sudo apt-get update
Now type sudo apt-get install amsn
now open amsn. If it works then go back to the the start and un-tick the Hardy-Proposed box
now in that same shell type sudo apt-get update to get back where you were.


OUTPUT of 
$ sudo apt-get update
Ign [http://repoubuntusoftware.info](http://repoubuntusoftware.info) harty Release.gpg
Ign [http://repoubuntusoftware.info](http://repoubuntusoftware.info) harty/all Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Translation-en_US
Ign [http://repoubuntusoftware.info](http://repoubuntusoftware.info) harty Release
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/universe Translation-en_US
Ign [http://repoubuntusoftware.info](http://repoubuntusoftware.info) harty/all Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages
Hit [http://repoubuntusoftware.info](http://repoubuntusoftware.info) harty/all Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/multiverse Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/restricted Sources

---

### Post by Naatan on 2008-08-18
Are you sure the update manager is enabled?

Click System > Administration > Synaptic Package Manager
Click on Settings > Repositories
Go to the Updates tab.
Make sure "Check for updates" is checked and preferrably check "Daily"

---

### Post by Andybr2000 on 2008-08-19
I tried that before, and I still have the same problem.Also, I uninstall and install the update manager. I got some errors on the update manager. Where is the error logs?

---

### Post by Naatan on 2008-08-19
/var/log/apt/term.log

What happens when you open the Update Manager manually?

---

### Post by Andybr2000 on 2008-08-19
I did not have problems with open update manager 
That is my log file term.log

Log started: 2008-08-12  21:41:01
(Reading database ... 192164 files and directories currently installed.)

Preparing to replace initramfs-tools 0.85eubuntu39.1 (using .../initramfs-tools_0.85eubuntu39.2_all.deb) ...

Unpacking replacement initramfs-tools ...

Preparing to replace update-manager 1:0.87.27 (using .../update-manager_1%3a0.87.30_all.deb) ...

Unpacking replacement update-manager ...

Preparing to replace update-manager-core 1:0.87.27 (using .../update-manager-core_1%3a0.87.30_i386.deb) ...

Unpacking replacement update-manager-core ...

Preparing to replace app-install-data-commercial 9 (using .../app-install-data-commercial_9.2_all.deb) ...

Unpacking replacement app-install-data-commercial ...

Preparing to replace kdenetwork-filesharing 4:3.5.9-0ubuntu1 (using .../kdenetwork-filesharing_4%3a3.5.9-0ubuntu1.1_i386.deb) ...

Unpacking replacement kdenetwork-filesharing ...

Preparing to replace kdenetwork-kfile-plugins 4:3.5.9-0ubuntu1 (using .../kdenetwork-kfile-plugins_4%3a3.5.9-0ubuntu1.1_i386.deb) ...

Unpacking replacement kdenetwork-kfile-plugins ...

Preparing to replace kdnssd 4:3.5.9-0ubuntu1 (using .../kdnssd_4%3a3.5.9-0ubuntu1.1_i386.deb) ...

Unpacking replacement kdnssd ...

Preparing to replace kopete 4:3.5.9-0ubuntu1 (using .../kopete_4%3a3.5.9-0ubuntu1.1_i386.deb) ...

Unpacking replacement kopete ...

Preparing to replace kpf 4:3.5.9-0ubuntu1 (using .../kpf_4%3a3.5.9-0ubuntu1.1_i386.deb) ...

Unpacking replacement kpf ...

Preparing to replace kppp 4:3.5.9-0ubuntu1 (using .../kppp_4%3a3.5.9-0ubuntu1.1_i386.deb) ...

Unpacking replacement kppp ...

Preparing to replace krdc 4:3.5.9-0ubuntu1 (using .../krdc_4%3a3.5.9-0ubuntu1.1_i386.deb) ...

Unpacking replacement krdc ...

Preparing to replace krfb 4:3.5.9-0ubuntu1 (using .../krfb_4%3a3.5.9-0ubuntu1.1_i386.deb) ...

Unpacking replacement krfb ...

Preparing to replace libnspr4-0d 4.7.1+1.9-0ubuntu0.8.04.1 (using .../libnspr4-0d_4.7.1+1.9-0ubuntu0.8.04.5_i386.deb) ...

Unpacking replacement libnspr4-0d ...

Preparing to replace libnss3-1d 3.12.0.2+1.9-0ubuntu0.8.04.1 (using .../libnss3-1d_3.12.0.3-0ubuntu0.8.04.4_i386.deb) ...

Unpacking replacement libnss3-1d ...

Preparing to replace libnss3-0d 3.12.0.2+1.9-0ubuntu0.8.04.1 (using .../libnss3-0d_3.12.0.3-0ubuntu0.8.04.4_i386.deb) ...

Unpacking replacement libnss3-0d ...

Preparing to replace openoffice.org-writer2latex 0.5-6 (using .../openoffice.org-writer2latex_0.5-6ubuntu0.1_all.deb) ...

Removing extension org.openoffice.legacy.writer2latex.uno.pkg... done.

Unpacking replacement openoffice.org-writer2latex ...

Preparing to replace update-notifier-common 0.70.7 (using .../update-notifier-common_0.70.9_all.deb) ...

Unpacking replacement update-notifier-common ...

Preparing to replace update-notifier 0.70.7 (using .../update-notifier_0.70.9_i386.deb) ...

Unpacking replacement update-notifier ...

Setting up initramfs-tools (0.85eubuntu39.2) ...

update-initramfs: deferring update (trigger activated)



Setting up update-manager-core (1:0.87.30) ...



Setting up update-manager (1:0.87.30) ...



Setting up app-install-data-commercial (9.2) ...

Caching application data...

Generating mime/codec maps...



Setting up kdenetwork-filesharing (4:3.5.9-0ubuntu1.1) ...



Setting up kdenetwork-kfile-plugins (4:3.5.9-0ubuntu1.1) ...

Setting up kdnssd (4:3.5.9-0ubuntu1.1) ...

Setting up kopete (4:3.5.9-0ubuntu1.1) ...



Setting up kpf (4:3.5.9-0ubuntu1.1) ...



Setting up kppp (4:3.5.9-0ubuntu1.1) ...



Setting up krdc (4:3.5.9-0ubuntu1.1) ...



Setting up krfb (4:3.5.9-0ubuntu1.1) ...



Setting up libnspr4-0d (4.7.1+1.9-0ubuntu0.8.04.5) ...



Setting up libnss3-1d (3.12.0.3-0ubuntu0.8.04.4) ...



Setting up libnss3-0d (3.12.0.3-0ubuntu0.8.04.4) ...



Setting up openoffice.org-writer2latex (0.5-6ubuntu0.1) ...

Adding extension /usr/lib/openoffice/share/extension/install/writer2latex.uno.pkg... done.



Setting up update-notifier-common (0.70.9) ...

Setting up update-notifier (0.70.9) ...



Processing triggers for initramfs-tools ...

update-initramfs: Generating /boot/initrd.img-2.6.24-19-generic

Processing triggers for libc6 ...

ldconfig deferred processing now taking place

Log ended: 2008-08-12  21:43:59

Log started: 2008-08-18  22:00:24
(Reading database ... 192172 files and directories currently installed.)

Removing ubuntu-desktop ...

Removing update-notifier ...

Purging configuration files for update-notifier ...

Removing update-manager ...

Purging configuration files for update-manager ...

Log ended: 2008-08-18  22:01:16

Log started: 2008-08-18  22:02:06
Selecting previously deselected package update-manager.

(Reading database ... 192023 files and directories currently installed.)

Unpacking update-manager (from .../update-manager_1%3a0.87.30_all.deb) ...

Selecting previously deselected package update-notifier.

Unpacking update-notifier (from .../update-notifier_0.70.9_i386.deb) ...

Setting up update-manager (1:0.87.30) ...



Setting up update-notifier (0.70.9) ...



Log ended: 2008-08-18  22:02:20

---

### Post by Andybr2000 on 2008-08-20
I think the update manager stop working after the upgrade to latest version. How can I install the older version?

Upgraded the following packages:
app-install-data-commercial (9) to 9.2
initramfs-tools (0.85eubuntu39.1) to 0.85eubuntu39.2
kdenetwork-filesharing (4:3.5.9-0ubuntu1) to 4:3.5.9-0ubuntu1.1
kdenetwork-kfile-plugins (4:3.5.9-0ubuntu1) to 4:3.5.9-0ubuntu1.1
kdnssd (4:3.5.9-0ubuntu1) to 4:3.5.9-0ubuntu1.1
kopete (4:3.5.9-0ubuntu1) to 4:3.5.9-0ubuntu1.1
kpf (4:3.5.9-0ubuntu1) to 4:3.5.9-0ubuntu1.1
kppp (4:3.5.9-0ubuntu1) to 4:3.5.9-0ubuntu1.1
krdc (4:3.5.9-0ubuntu1) to 4:3.5.9-0ubuntu1.1
krfb (4:3.5.9-0ubuntu1) to 4:3.5.9-0ubuntu1.1
libnspr4-0d (4.7.1+1.9-0ubuntu0.8.04.1) to 4.7.1+1.9-0ubuntu0.8.04.5
libnss3-0d (3.12.0.2+1.9-0ubuntu0.8.04.1) to 3.12.0.3-0ubuntu0.8.04.4
libnss3-1d (3.12.0.2+1.9-0ubuntu0.8.04.1) to 3.12.0.3-0ubuntu0.8.04.4
openoffice.org-writer2latex (0.5-6) to 0.5-6ubuntu0.1
update-manager (1:0.87.27) to 1:0.87.30
update-manager-core (1:0.87.27) to 1:0.87.30
update-notifier (0.70.7) to 0.70.9
update-notifier-common (0.70.7) to 0.70.9

---

### Post by happycoder on 2008-08-24
I am running 8.04 and I haven't seen any updates for more than a week. It took me awhile to notice.

I used to get updates every day. I've tried switching software sources from the US server to the main server, but behavior is the same. The /var/log/apt/term.log hasn't been updated since 2008-08-11. It doesn't seem to contain any errors, and I don't see any errors in syslog. I have not installed any new software this month.

When I switched back to the United States server, the icon appeared in the tool bar, but went away immediately after it finished. Still no updates. When I run sudo apt-get update it looks the same as shown in Andybr2000's post.

Is there a problem with the update manager? What information should I provide?

Thanks in advance for your help.

---

### Post by kaaino on 2008-08-25
Hi,

I have the same problem: no updates since a couple of weeks.

I have just tried to downgrade the update manager to the previous version. The old version cannot find any update as well, except than the update-manager itself.

So, my conclusion is that everything is working but there are just no updates..... these ubuntu boys are becoming lazy :)

---

### Post by EvilDarkElf on 2008-08-25
Same here. No updates in weeks (and I update fanatically; Synaptic checks daily and I check manually at least every 2 days). A colleague noticed the same thing. 

Does anyone know if there is a thread somewhere that could verify/dismiss kaaino's hypothesis? Or maybe something in Launchpad? I would hate so spend days trying to fix a problem that doesn't exist.

---

### Post by xSauronx on 2008-08-25
> **kaaino said:**
> Hi,

I have the same problem: no updates since a couple of weeks.

I have just tried to downgrade the update manager to the previous version. The old version cannot find any update as well, except than the update-manager itself.

So, my conclusion is that everything is working but there are just no updates..... these ubuntu boys are becoming lazy :)

i had to change the repo i was using the other day because i couldnt get updates. 

the US server selected via synaptic was no good and i switched it to main. give that a shot.

---

### Post by happycoder on 2008-08-25
I asked the Software Sources dialog to select the best server. It checked over 200 potential candidates and picked one in Texas. It seemed to be behaving in a reasonable manner. This makes three repositories I've tried. I still have no updates. 

I haven't been able to figure out how to manually check the repositories for updates. Given the rate they usually come at, I'd be surprised if there weren't any.

---

### Post by happycoder on 2008-08-26
No changes to system, got critical kernel updates today. Perhaps there is no problem? Or I'm getting only some updates?

I spent some time reading but haven't figured out how to manually determine if there are updates that I'm missing. The timestamps on the repository led me to believe there were.

---

