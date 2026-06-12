---
title: "apt repos not signed"
date: 2009-10-19
forum: Installation &amp; Upgrades
---

### Post by superbenny on 2009-10-19
i recently installed easy peasy on my brand new, beautiful 1005HA, and everything works perfectly...except about half the software repos...whenever i try to update (in synaptic, or via apt-get update), i get the following:

```
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://us.archive.ubuntu.com jaunty Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: GPG error: http://apt.jolicloud.org robby Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 356BB697B8B45DD0
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jaunty/Release
```

I can't open the repo manager through synaptic>settings>repositories or through administration>software sources

jolicloud can't download/install the software either.

---

### Post by stlsaint on 2009-10-19
have you tried adding the keys manually. im not on my home machine right now so i cant reference but try and visit ubuntu website and see about adding keys.

---

### Post by superbenny on 2009-10-19
I have not. I'll try that now. On a possibly related note, when I try to run the Software Sources "app" from the command line, I get this:

    app = SoftwarePropertiesGtk(datadir=data_dir, options=options, file=file)
  File "/usr/lib/python2.6/dist-packages/softwareproperties/gtk/SoftwarePropertiesGtk.py", line 75, in __init__
    SoftwareProperties.__init__(self, options=options, datadir=datadir)
  File "/usr/lib/python2.6/dist-packages/softwareproperties/SoftwareProperties.py", line 83, in __init__
    self.reload_sourceslist()
  File "/usr/lib/python2.6/dist-packages/softwareproperties/SoftwareProperties.py", line 521, in reload_sourceslist
    self.distro.get_sources(self.sourceslist)    
  File "/usr/lib/python2.6/dist-packages/aptsources/distro.py", line 90, in get_sources
    raise NoDistroTemplateException("Error: could not find a "
aptsources.distro.NoDistroTemplateException: Error: could not find a distribution template

---

### Post by superbenny on 2009-10-19
> **stlsaint said:**
> have you tried adding the keys manually. im not on my home machine right now so i cant reference but try and visit ubuntu website and see about adding keys.
Just added the gpg key that it said it was having issues with. Now after running sudo apt-get update, I get this:

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/Release](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems

sooo...same as before.

---

### Post by stlsaint on 2009-10-19
exactly what key did you add?

---

### Post by superbenny on 2009-10-20
> **stlsaint said:**
> exactly what key did you add?

i did

gpg --keyserver subkeys.pgp.net --recv-keys 40976EAF437D05B5

which translated to 437D05B5, apparently.

whatever it was, it was successful, but it didn't help anything.

---

### Post by stlsaint on 2009-10-20
run this sequence in terminal:

```
apt-get clean
cd /var/lib/apt
mv lists lists.old
mkdir -p lists/partial
apt-get clean
apt-get update
```

---

