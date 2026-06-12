---
title: "Upgrade from 8.04 to 8.10 via alternate CD"
date: 2008-10-31
forum: General Help
---

### Post by EpidemikE on 2008-10-31
Hey,

Last night I did an upgrade from the the alternate CD and everything seems to have went accordingly and smoothly. The only area I am having some issues is with synaptic and the repositories.

I changed all of the repositories I have from hardy to intrepid. After doing this I tried to reinstall Amarok and it prompted me for the CD. I dont have the CD with me since I left at home. I then decided that I would try and force the repo instead of the CD by unchecking the CD box in the sources list.

Any idea what I did and how I can go about correcting it?

Here is the error(s):
> W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/r/ruby1.8/libruby1.8_1.8.7.72-1_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/r/ruby1.8/libruby1.8_1.8.7.72-1_amd64.deb)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/r/ruby1.8/ruby1.8_1.8.7.72-1_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/r/ruby1.8/ruby1.8_1.8.7.72-1_amd64.deb)
  
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/r/ruby-defaults/ruby_4.2_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/r/ruby-defaults/ruby_4.2_all.deb)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/a/amarok/amarok-common_1.4.10-0ubuntu3_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/a/amarok/amarok-common_1.4.10-0ubuntu3_all.deb)
  
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/a/arts/libartsc0_1.5.10-0ubuntu1_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/a/arts/libartsc0_1.5.10-0ubuntu1_amd64.deb)
  
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/q/qt-x11-free/libqt3-mt_3.3.8-b-5ubuntu1_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/q/qt-x11-free/libqt3-mt_3.3.8-b-5ubuntu1_amd64.deb)
  
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/a/arts/libarts1c2a_1.5.10-0ubuntu1_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/a/arts/libarts1c2a_1.5.10-0ubuntu1_amd64.deb)
  
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-qt3-1_0.6.23-2ubuntu2_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-qt3-1_0.6.23-2ubuntu2_amd64.deb)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/l/lua50/liblua50_5.0.3-3_amd64.deb\](http://us.archive.ubuntu.com/ubuntu/pool/main/l/lua50/liblua50_5.0.3-3_amd64.deb\)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/l/lua50/liblualib50_5.0.3-3_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/l/lua50/liblualib50_5.0.3-3_amd64.deb)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdelibs/kdelibs-data_3.5.10-0ubuntu6_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdelibs/kdelibs-data_3.5.10-0ubuntu6_all.deb)
  
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdelibs/kdelibs4c2a_3.5.10-0ubuntu6_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdelibs/kdelibs4c2a_3.5.10-0ubuntu6_amd64.deb)
  
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/a/amarok/amarok-engine-xine_1.4.10-0ubuntu3_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/a/amarok/amarok-engine-xine_1.4.10-0ubuntu3_amd64.deb)
  
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libi/libifp/libifp4_1.0.0.2-3_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libi/libifp/libifp4_1.0.0.2-3_amd64.deb)
  
W: Failed to fetch cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081028)]/pool/main/libm/libmtp/libmtp8_0.3.0-1ubuntu1_amd64.deb
  
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libn/libnjb/libnjb5_2.2.5-4.2ubuntu1_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libn/libnjb/libnjb5_2.2.5-4.2ubuntu1_amd64.deb)
  
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libt/libtunepimp/libtunepimp5_0.5.3-7ubuntu3_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libt/libtunepimp/libtunepimp5_0.5.3-7ubuntu3_amd64.deb)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/a/amarok/amarok_1.4.10-0ubuntu3_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/a/amarok/amarok_1.4.10-0ubuntu3_amd64.deb)

---

### Post by EpidemikE on 2008-10-31
Any suggestions? sorry to bump up the thread.

---

### Post by drs305 on 2008-10-31
I am getting access to the sites you posted although slowly. Have you tried changing the server via Synaptic, Settings, Repositories > Downoad From, Select Best Server. At least temporarily, you may find a less-used server faster as the servers will be heavily taxed due to the new release.

Unchecking the cdrom, if you can't insert it, was the correct thing to do and should not be the cause of your current problems as long as you can connect to a server.

---

### Post by EpidemikE on 2008-11-03
drs305, I had it set to the US server and I am going try with it set to Main server. I will let you know what happens.

EDIT:

Here is what I am getting now as an "error"

From synaptic
```
E: I wasn't able to locate file for the libruby1.8 package. This might mean you need to manually fix this package.

```

```
amarok:

Package amarok has no available version, but exists in the database.
This typically means that the package was mentioned in a dependency and never uploaded, has been obsoleted or is not available with the contents of sources.list
```

EDIT2: 
This is really starting to perturb me. I dunno why it keeps looking for the CD.

```
W: Failed to fetch cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081028)]/dists/intrepid/main/binary-amd64/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081028)]/dists/intrepid/restricted/binary-amd64/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

```

---

### Post by drs305 on 2008-11-03
I have both those packages in my synaptic listings. In Settings, Repositories, Software Sources I have main, restricted, universer and multiverse ticked. I checked at [http://packages.ubuntu.com/]("http://packages.ubuntu.com/") and both should be in the repositories if you have them selected.

While you are in synaptic, go the the left filter pane and search for broken packages. If they are listed, there is an option to Fix Broken Packages in the top menu.

You have to disable the CD. On the main repository page in synaptic or software sources, untick the CD in the lower window. Otherwise it will always look for the CD at the beginning of a search and ask you to insert it.

If the repositories weren't previously ticked, hit the Reload button or run:
```

sudo apt-get update && sudo apt-get upgrade

```

---

### Post by EpidemikE on 2008-11-03
I think I have solved this. It looks like my list of 3rd party repos was giving me the issue since I removed all of them and I was able to download software via synaptic.

Thanks for your help.

---

