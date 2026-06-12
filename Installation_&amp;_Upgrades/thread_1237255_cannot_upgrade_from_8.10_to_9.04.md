---
title: "cannot upgrade from 8.10 to 9.04"
date: 2009-08-11
forum: Installation &amp; Upgrades
---

### Post by rambentuvia on 2009-08-11
I get a fail message with this text.
I am experiencing other issues that I think are related:
every 9.04 iso I try to download I get an incorrect md5sum (this happens when I download from various sites and on various machines with various operating systems (xp vista and ubuntu)

Anyone can help
 
Failed to fetch [http://il.archive.ubuntu.com/ubuntu/pool/main/s/samba/smbclient_3.3.2-1ubuntu3.1_i386.deb](http://il.archive.ubuntu.com/ubuntu/pool/main/s/samba/smbclient_3.3.2-1ubuntu3.1_i386.deb) Hash Sum mismatch
Failed to fetch [http://il.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-core_3.0.1-9ubuntu3_i386.deb](http://il.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-core_3.0.1-9ubuntu3_i386.deb) Hash Sum mismatch
Failed to fetch [http://il.archive.ubuntu.com/ubuntu/pool/main/o/openssl-blacklist/openssl-blacklist_0.4.2ubuntu1_all.deb](http://il.archive.ubuntu.com/ubuntu/pool/main/o/openssl-blacklist/openssl-blacklist_0.4.2ubuntu1_all.deb) Hash Sum mismatch
Failed to fetch [http://il.archive.ubuntu.com/ubuntu/pool/main/e/example-content/example-content_36_all.deb](http://il.archive.ubuntu.com/ubuntu/pool/main/e/example-content/example-content_36_all.deb) Hash Sum mismatch
Failed to fetch [http://il.archive.ubuntu.com/ubuntu/pool/main/g/gnome-games/gnome-games-data_2.26.1-0ubuntu2_all.deb](http://il.archive.ubuntu.com/ubuntu/pool/main/g/gnome-games/gnome-games-data_2.26.1-0ubuntu2_all.deb) Hash Sum mismatch
Failed to fetch [http://il.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org-dictionaries/openoffice.org-thesaurus-en-us_3.0.1-8ubuntu1_all.deb](http://il.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org-dictionaries/openoffice.org-thesaurus-en-us_3.0.1-8ubuntu1_all.deb) Hash Sum mismatch
Failed to fetch [http://il.archive.ubuntu.com/ubuntu/pool/universe/t/ttf-kochi/ttf-kochi-mincho_1.0.20030809-8_all.deb](http://il.archive.ubuntu.com/ubuntu/pool/universe/t/ttf-kochi/ttf-kochi-mincho_1.0.20030809-8_all.deb) Hash Sum mismatch
Failed to fetch [http://il.archive.ubuntu.com/ubuntu/pool/multiverse/m/mplayer/mencoder_1.0~rc2-0ubuntu19_i386.deb](http://il.archive.ubuntu.com/ubuntu/pool/multiverse/m/mplayer/mencoder_1.0~rc2-0ubuntu19_i386.deb) Hash Sum mismatch

---

### Post by chamira on 2009-08-11
Not sure about the hash mismatch, but why don't you use the upgrade manager. I managed to get from 8.04 to 9.04 via 8.10 within Ubuntu. You need to configure the update settings to allow for all scheduled updates I think. Sorry I can't be more definite with the instructions - currently at work using Windows.

Here are teh instructions I followed: [http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

---

### Post by rambentuvia on 2009-08-11
This was the result from the update manager. I did not run all the updates on 8.10 because I get failures there too. I will run the updates on 8.10 and post them

---

### Post by Partyboi2 on 2009-08-11
> **rambentuvia said:**
> This was the result from the update manager. I did not run all the updates on 8.10 because I get failures there too. I will run the updates on 8.10 and post them
Hi, try changing your download server under Software Sources to another one.

---

### Post by slakkie on 2009-08-11
Could you run the following:

sudo aptitude update && sudo aptitude -s safe-upgrade

if you agree with the changes:
sudo aptitude -y safe-upgrade

sudo aptitude install update-manager-core
sudo do-release-upgrade

---

