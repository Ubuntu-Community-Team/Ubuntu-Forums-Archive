---
title: "Paint Shop Pro"
date: 2005-11-06
forum: General Help
---

### Post by nSTKo on 2005-11-06
Hi!
Can somebody help me...
I realy need Paint Shop Pro in Ubuntu, is there any way to "lift it off"?

All my ideas.
It isnt working with Wine. ("lift off with wine")
I don't know how to compile VMWare. (run winxp with vmware)

---

### Post by poptones on 2005-11-06
It's not exactly the same, I know, but if you will install inkscape I believe you will find the two together (gimp and inkscape) offer the same functionality.

---

### Post by kingzasz on 2005-11-06
There is no way that I have found.  I havn't tried VMWare yet though.

My current solution is to use krdc to open up a vnc session with a windows computer on my network.  PSP is installed on that computer.

---

### Post by pickarooney on 2005-11-06
Does anyone know if gimpshop (mod of gimp to make the layout more PS-like) is available for Ubuntu?

Also, is there any way to dock all the windows in the gimp? I find it completely unusable the way it's set up by default, with twenty separate windows opening and hiding under one another.

---

### Post by BIGtrouble77 on 2005-11-06
vmware is pretty easy to install in breezy.  
This pretty much sums it up (copied from another thread):
```

sudo apt-get install build-essential linux-headers-`uname -r`
sudo apt-get install gcc-3.4 g++-3.4
export CC=/usr/bin/gcc-3.4

# download vmware

tar xvzf VMware-workstation-5.0.0-13124.tar.gz
cd vmware-distrib

# say "No" when asked to run vmware-config.pl
sudo ./vmware-install.pl

# download the vmware-any-any-update script
# http://platan.vc.cvut.cz/ftp/pub/vmware/
tar xvzf vmware-any-any-update94.tar.gz
cd vmware-any-any-update94

# say "Yes" at the end of ./runme.pl
sudo ./runme.pl
```

I recommend installing winme over winxp or win2k.  It's MUCH faster.  You can even play a good amount of 2d games.  I had problems with all of the win98 flavors.

I'd also recommend against gimpshop.  I haven't found it in any of the repositories, but it's probably better to use gimp as it should be.  A very substantial release is coming for gimp, so you'll really want to use that when it comes out.

---

