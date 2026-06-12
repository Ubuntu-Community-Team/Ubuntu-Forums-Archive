---
title: "just wanted to get some minimum server hardware opinions"
date: 2008-06-24
forum: Hardware
---

### Post by mowgliee on 2008-06-24
i use ubuntu to run a basic LAN server (dhcp, ldap, file sharing, print server, router, firewall, nfs) over a 10/100 network with 20 ubuntu clients & T1 internet pipe.  i have a dell poweredge 400sc p4 2/4 ghz w/ 1 gb pc3200 ddram.  is that overkill?

if i downgrade to a dell optiplex gx110 p3 800 mhz w/ 512 mb sdram, would my clients notice a performance difference considering the services and LAN size?

will use latest ubuntu on all servers/clients.

thanx.

---

### Post by ukripper on 2008-06-24
> **mowgliee said:**
> i use ubuntu to run a basic LAN server (dhcp, ldap, file sharing, print server, router, firewall, nfs) over a 10/100 network with 20 ubuntu clients & T1 internet pipe.  i have a dell poweredge 400sc p4 2/4 ghz w/ 1 gb pc3200 ddram.  is that overkill?

if i downgrade to a dell optiplex gx110 p3 800 mhz w/ 512 mb sdram, would my clients notice a performance difference considering the services and LAN size?

will use latest ubuntu on all servers/clients.

thanx.

depends on what clients are/will be using applications wise.

---

### Post by mowgliee on 2008-06-24
clients will use openoffice suite of apps, firefox, file browser, skype, xmms, vlc media player for video, terminals, image viewers, adobe reader, perhaps some gimp ... thats about it.

but these are all thick/fat clients; all software is installed locally, not served from server (except for those basic services i mentioned originally).  i'm not using ltsp or anything like that.

---

### Post by ukripper on 2008-06-25
> **mowgliee said:**
> clients will use openoffice suite of apps, firefox, file browser, skype, xmms, vlc media player for video, terminals, image viewers, adobe reader, perhaps some gimp ... thats about it.

but these are all thick/fat clients; all software is installed locally, not served from server (except for those basic services i mentioned originally).  i'm not using ltsp or anything like that.

Then it should be fine with your 800mhz server option for fat clients but allow bit more swap. But if you require any database based application putting quite a load on the server then your first option is appropriate. 

If you are going to use backup server at some point i would go for your first option to backup, 20 machines you do need good bandwidth and good system spec with hardware or software RAID.

goodluck.

---

### Post by mowgliee on 2008-06-25
ok makes sense.  i wont be using any dbase apps since its just a local LAN server (unless you consider ldap but i dont think thats what you meant).  all my dbase apps are web based and i use another, better server for that.

as for backup, i have each server do nightly zipped tarballs of the vital dirs & files.  then i have another backup server/box which scp's the bz files to itself nightly.  no one else uses this backup box so i presume its ok being a dumpy 800 mhz cpu as well.

i havent explored RAID yet, but i imagine its to make real time dupe of my primary hard disk?  and that 2nd disk serves as a live fall back in case of failure of the 1st?  i imagine this constant "backing up" would eat considerable resources and i would need better cpu, ram, & hd?

---

