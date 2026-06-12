---
title: "Samba stopped working"
date: 2008-07-23
forum: General Help
---

### Post by esaym on 2008-07-23
Ok funny thing.  

My friend runs kubuntu and he uses samba through dolphin to browse the windows network shares.  Particularly this is how he shares files between his windows vmware session on his machine.  Well now just today trying to browse for network shares in either konqueror or dolphin just leads to a blank directory and nothing ever shows up.  I ran a network scanner and I see connections coming and going to his computer on ports 137 and 138 so something is working.  Any ideas what is going on?  He restarted the machine a few times and that didn't help.  

Sam
Kubuntu 7.10

---

### Post by esaym on 2008-07-24
Oh dear no responses.  Well I will try to check the system out better and post back later with anything I find.  I pretty much know nothing about samba.  I have never had to mess with it, it was always able to browse the network out of the box.

---

### Post by orrorin on 2008-07-24
What does ```
sudo smbstatus
``` show?

---

### Post by esaym on 2008-07-24
> **orrorin said:**
> What does ```
sudo smbstatus
``` show?

root@desktop:~# smbstatus

Samba version 3.0.26a
PID     Username      Group         Machine
-------------------------------------------------------------------

Service      pid     machine       Connected at
-------------------------------------------------------

No locked files

---

### Post by orrorin on 2008-07-24
> **esaym said:**
> root@desktop:~# smbstatus

Samba version 3.0.26a
PID     Username      Group         Machine
-------------------------------------------------------------------

Service      pid     machine       Connected at
-------------------------------------------------------

No locked files

I'm not sure if this is the output from the machine where the samba server is running. Sorry for not clarifying earlier.

Pl. run smbstatus on the machine which runs the samba server (after you map the share on the other machine). If it does not show any username, etc then the login itself is not going through -- in which case check if you are providing the correct credentials (or if you are using a credential file, check if it has the right permissions).

If it shows the correct username, then something else is messed up. 

If possible run wireshark and do a packet capture. In the filter window for wireshark (which is the long horizontal bar like window towards top left), type 'smb'; this will display only SMB protocol messages. Then look for TRANS2 Find_First2 (FF2) and Find_Next2 (FN2) requests and responses. Check if they indicate any errors. If no errors, then you might also be able to see the list of files in the dir which you are trying to browse. If you see files listed in the payload, then everything is fine from the samba side and the problem lies elsewhere.

---

### Post by esaym on 2008-07-26
Well there is no samba server.  There are a couple of windows boxes and one vmware windows machine on the network.  But by going to samba shares in (k)ubuntu he is able to browse those shares.  He says sometimes it stops working and a simple restart usually gets it working again.  He restarted the ubuntu machine several times and he could still not browse anything.  BUT the good news is that after 2 days of that it magically started working again.  So now I don't have anything to trouble shoot.  But when it happens again I will do your tests like you mentioned.


Thanks

---

### Post by orrorin on 2008-07-27
Sorry ... I had mis-read your post.

If the problem recurs, he can run wireshark on the windows machines as well to trace how far the protocol is going.

---

