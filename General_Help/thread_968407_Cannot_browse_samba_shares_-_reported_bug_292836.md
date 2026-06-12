---
title: "Cannot browse samba shares - reported bug 292836"
date: 2008-11-02
forum: General Help
---

### Post by WrathofthePenguin on 2008-11-02
Hi all - 

I've reported the following bug for the inability to browse samba shares. One workaround that has been proposed was to use Gnome Commander - this only works to a limited degree - see the bug report (link below).

In my opinion this is a bug with Samba - the packets being sent back to the samba server are sent with the last character of the requested directory file dropped and the server sends back an error that it cannot find it. This is why some of you may have noticed that *some* things showed up. If the files "windowsxpisforchumps" and "windowsxpisforchumps2" are in the share, they will show up in Gnome Commander. They will not show up in a share opened with Places->Connect to server - this method apparently won't show files that it doesn't get path info on (the traces for both Gnome Commander and this method are very similar - Gnome Commander just has lower standards ;)  )


[https://bugs.launchpad.net/ubuntu/+bug/292836](https://bugs.launchpad.net/ubuntu/+bug/292836)

---

### Post by WrathofthePenguin on 2008-11-02
I posted the following in another thread also, but I'm putting it here so it's easy to find:

Open the share up in firefox and add the last character of directories/files in the url bar.

Example:

If I open up my share using:

smb://192.168.5.103/

And click on the share name (for me it's Volume_1), I get this in the url bar:

smb://192.168.5.103/Volume_1

Look at the files and directories below, they will all have the last character dropped. Click on one anyway. I clicked on "DVDs" and the following shows up in the url bar:

smb://192.168.5.103/Volume_1/DVD

I can add the 's' on to the end, and access the directory. I can keep doing this until I get where I need - it is very tedious, but it works.

---

### Post by WrathofthePenguin on 2008-11-18
The bug I submitted:

[https://bugs.launchpad.net/bugs/292836](https://bugs.launchpad.net/bugs/292836)

was marked as a duplicate of another:

[https://bugs.launchpad.net/bugs/282298](https://bugs.launchpad.net/bugs/282298)

The patch which fixes this bug is posted here:

[https://launchpad.net/~tcarrez/+archive](https://launchpad.net/~tcarrez/+archive)

And it resolved the problem completely for me.

To install:

In Synaptic Package Manager, go to Settings->Repositories

Under the Third-Party Software tab, click on Add.

Enter the following:

deb [http://ppa.launchpad.net/tcarrez/ubuntu](http://ppa.launchpad.net/tcarrez/ubuntu) intrepid main

and Click on Add Source.

You can reload and the update shows up for samba (there will be a little star showing for Samba. You can click and upgrade. Do all the upgrades and make sure there aren't others for Samba afterward.

---

