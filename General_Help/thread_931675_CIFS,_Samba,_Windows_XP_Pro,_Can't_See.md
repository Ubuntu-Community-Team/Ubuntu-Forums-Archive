---
title: "CIFS, Samba, Windows XP Pro, Can't See"
date: 2008-09-27
forum: General Help
---

### Post by claytoncramer on 2008-09-27
Back in Ubuntu 6.06, Samba worked great for letting me see my Windows XP files.  I used this primarily so that I could backup my modified files every day.  I ran out of disk space on the decrepit desktop that I was using for this, so I stopped worrying about this. 

Now I have taken a very fast notebook and installed Hardy Heron 8.04, and I am running into some problems.  Samba has been replaced by CIFS, as near as I can tell.  Everything works just fine for getting access to files on my wife's Windows XP box--but when I try to do the same sequence of steps to get to the files on my Windows XP Professional box--no luck!  

sudo mount -t cifs //rhonda/My\ Documents /home/clayton/rhondalink -o guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777

That works great!  But when I do the same command 

sudo mount -t cifs //claytonnotebook/My\ Documents /home/clayton/claytonnotebooklink -o guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777

I get:

mount error: could not find target server.  TCP name claytonnotebook/My Documents not found

My first assumption was that there was a sharing problem on my XP Pro box.  Nope.  When I do an smbtree, it shows the rhonda desktop (which is XP Home Edition), but not the XP Pro notebook.

So the next step was to try and ping the XP Pro notebook.  I tried both by name and by IP address--and neither responds.  Now, the lack of response by name would suggest that I don't have the /etc/nsswitch.conf file set up correctly--but the lack of response by IP address (which I know is the correct address) suggests that XP Pro may have some security stuff turned on that prevents it from responding.

The /etc/nsswitch.conf file's hosts: line is:

hosts:     files wins dns mdsn4_minimal [NOTFOUND=return] mdns4

I've turned off just about every security setting that the XP Pro notebook has set: Windows Firewall is off.  I've turned off the Symantec IP filtering feature in the networking stack.  I've tried a number of suggestions that I have found around the web.  Help!

UPDATE: a little more detail.  I tried this from the decrepit workstation that is also running Hardy Heron, and I noticed this rather interesting, but different message when I ran smbtree:

MSHOME
        \\UBUNTU-LAPTOP                 ubuntu-laptop server (Samba, Ubuntu)
                \\UBUNTU-LAPTOP\4100mfp         4100mfp
                \\UBUNTU-LAPTOP\PDF             PDF
                \\UBUNTU-LAPTOP\IPC$            IPC Service (ubuntu-laptop server (Samba, Ubuntu))
                \\UBUNTU-LAPTOP\print$          Printer Drivers
        \\RHONDA                        RHONDA
                \\RHONDA\Owner
                \\RHONDA\C
                \\RHONDA\SharedDocs
                \\RHONDA\print$                 Printer Drivers
                \\RHONDA\IPC$                   Remote IPC
                \\RHONDA\My Documents
        \\CLAYTONNOTEBOOK               Clayton's notebook
cli_start_connection: failed to connect to CLAYTONNOTEBOOK<20> (0.0.0.0)
        \\CLAYTON-DESKTOP               clayton-desktop server (Samba, Ubuntu)
                \\CLAYTON-DESKTOP\ADMIN$                IPC Service (clayton-desktop server (Samba, Ubuntu))
                \\CLAYTON-DESKTOP\IPC$                  IPC Service (clayton-desktop server (Samba, Ubuntu))
                \\CLAYTON-DESKTOP\print$                Printer Drivers

What's with the cli_start_connection: failed to connect message?  It looks like someone is getting the wrong IP address.

---

### Post by Iowan on 2008-09-27
I doubt it's the issue, but just for information's sake:
Samba is still there - the Samba-server package must still be installed to share FROM an Ubuntu box.  **smbfs** is replaced by **cifs**, but the package SMBFS can be used to install it (confused yet??).

---

