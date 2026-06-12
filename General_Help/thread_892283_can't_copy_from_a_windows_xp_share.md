---
title: "can't copy from a windows xp share"
date: 2008-08-17
forum: General Help
---

### Post by indiv on 2008-08-17
I'm running Ubuntu 8.04 - the Hardy Heron, released in April 2008.  I've only installed a couple programs (dosbox, libc6-dev, vim, and imagemagick I think), and otherwise everything is default out of the box running in VMWare Workstation 5.5.4.  The network is shared such that the ubuntu system gets its own IP address from my router independently of the host machine (a Windows XP box).

**_Problem:_**

I have shared pictures on my Windows XP machine (the vmware host), each around 4-6 MB in size.  I've browsed to this shared folder in gnome by going to Places | Network -> Windows Network -> Dojo *[my workgroup]* -> ninja *[my Windows pc]* -> Pictures.

All the pictures show up as thumbnails in gnome (nautilus?).  I right click on the picture and click 'copy', then browse to a local folder and click 'paste'.

It works only rarely.  Most of the time it doesn't copy the files.  The copy operation fais and the GUI says, for example, 'Error while copying "IMG_0013.jpg.  There was an error copying the file into /home/indiv/Pictures.  <error>', with the options to cancel, skip all, or skip.  The errors I've received are 'invalid argument', 'connection timed out', 

Now when it fails like this, the copy pauses for about 5 seconds before failing.  When it succeeds, the copy finishes instantly with no delay.

Now moving to the command line, I do this (forgive minor typos as I'm typing the results rather than copy/paste):
**cp -f "/home/indiv/.gvfs/pictures on ninja/2008.03.01 - March/IMG_1130.jpg" .**

Same result as the GUI.  After anywhere from 6 to 20 seconds:
**cp: reading `/home/indiv/.gvfs/pictures on ninja/2008.03.01 - March/IMG_1130.jpg': Invalid argument**
or
**cp: reading `/home/indiv/.gvfs/pictures on ninja/2008.03.01 - March/IMG_1130.jpg': Input/output error**

Regardless of the GUI or command line, I'm always left with a partial copy of the image, anywhere from 1.5 MB to 3 MB in size.  The gnome thumbnail shows the top of the image with black on the bottom where the image is missing data.

I can't remember the exact command, but I tried running something like gvfs -r (again, I don't remember the exact command, sorry), which was supposed to print errors, but nothing printed when the copy failed.


**_Workaround:_**

Oddly enough, when I run the command through strace, it works every time.  I wrote a perl script that loops through all the directories on the Windows share and copies the files to the Ubuntu machine, and so far it hasn't failed with over 10 GB of data copied as long as I preface the copy with strace:

**strace cp -f "/home/indiv/.gvfs/pictures on ninja/2008.03.01 - March/IMG_1130.jpg" .**
<then it prints all the strace stuff, and when it's done, the file is complete and the copy worked>

If I modify this perl script I mentioned so that it doesn't use strace, it fails just about every time with the errors I mentioned above.  I'm guessing that it succeeds with strace because strace is slowing it down enough to where it's avoiding some sort of timeout.  But man, that's gotta be a tiny timeout.


**_Plea for help:_**

Anybody experience this?  Know what's wrong?  I'd be suprised if the traffic was even reaching my router considering I'm running ubuntu in a vmware session and these files I'm copying are on the host machine.  But even if something was going wonky and my network was going slower than normal (it's 100 Mbps), it can't be going *that* slow.

A google search has turned up naught, although I did find a bug report of a similar issue that was closed for lack of info.

---

### Post by indiv on 2008-08-17
OK, it looks like this is what's happening, but I have no idea why.  When I do a cp, SMB does this:

**ubuntu:**  SMB Read AndX Request for 65534 bytes.
**windows:**  SMB Read AndX Response for 65534 bytes.  The first packet contains 1385 bytes of the data.  The remaining 64KB of data comes in 1448-byte chunks of NBSS continuation packets.
**ubuntu:** SMB Read AndX Request for 1 byte.
**windows:** SMB Read AndX Response with 1 byte.  This SMB response packet is also the TCP ACK for the Read AndX Request.

This sequence repeats until ubuntu gets the entire file.  I'm guessing that cp is asking for 65535-byte chunks but the underlying SMB protocol layer is breaking it up into 65534 + 1.  When it fails (and remember that for some reason it never fails when I use strace), here's what happens.

... copying goes as normal until at some point ...
**ubuntu:** SMB Read AndX Request for 65534 bytes at some offset.
**windows:** SMB Read AndX Response plus NBSS Continuation packets.
**ubuntu:** SMB Read AndX Request for 1 byte at some offset.
**windows:** TCP ACK to the Read AndX Request.
<timeout>
**windows:** Closes the connection.

For some reason, the Windows XP system won't send a SMB Read AndX Response for some seemingly random request.  Ubuntu waits for the response, but Windows apparently times out and closes the connection with a RST-ACK.  That's when cp returns and prints an error to the console (although I'm unclear why I get varying error messages).

Also, **smbclient** doesn't work either (it has the same symptoms of copying a partial file) before failing for what it says is the same reason that cp fails (connection reset by the server):

[I]Domain=[NINJA] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]
getting file <truncated by me> read_socket_with_timeout:  timeout read.  read error = Connection reset by peer.
Receiving SMB:  Server stopped responding
Short read when getting file <truncated>.  Only got 3354624 bytes.
Error Read error: Connection reset by peer closing remote file
(3863.2 kb/s) (average 3863.2 kb/s)[/I]

... But when I run smbclient through strace, it works every time.  smbclient asks Windows for 64512-byte chunks, and when it fails, the same thing happens as I describe above.  smbclient asks for a 64512-byte chunk and Windows sends a TCP ACK for that request, but then never sends the SMB response with the data.

I'm puzzled.

---

### Post by lunchboxtheman on 2008-09-12
EDIT: Nevermind, even running through strace I can only copy 48KB or so of the file before I get a timeout.  Weird.  The machine I'm trying to pull from is running Vista(ugh) so that might be part of the problem.  What's weird is that I have to supply a user/pass even though I've allowed full access to the shared folder.  Just seems that samba is iffy to me.  Are there any alternatives?

I've been running linux for about a month now and really like it, too bad it doesn't work for anything useful.

---

### Post by Simon Cropper on 2008-09-20
I have also encountered this problem. 

I was trying to setup WINE to run some windows packages I just can seem to replace with Open Source / Linux alternatives. The error appears while trying to copy various DLL files from the Windows Share on my virtual Ubuntu machine setup on VMWare.

Running Ubuntu Hardy Heron on VMWare on XP Pro SP3. Accessing files with supported version of Samba.

[COLOR="Red"]I have been searching the forums and most posts appear to be about Vista-Ubuntu. All solutions suggest applying SP3 for Vista. Anyone encountered the problem on and have a solution for XP Pro?[/COLOR]

---

### Post by dhjdhj on 2008-10-06
I replaced Fedora 9 with Ubuntu 8 last weekend and ever since, I have seen exactly the same problem whenever I try to copy files from my Macintosh to Fedora. I've tried both SAMBA and scp --- both fail on large files.

I never had the problem with my Fedora distro.

---

