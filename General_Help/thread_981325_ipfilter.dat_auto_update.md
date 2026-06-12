---
title: "ipfilter.dat auto update"
date: 2008-11-13
forum: General Help
---

### Post by Ledger on 2008-11-13
Hi

I'm running µTorrent at Ubuntu 8.10 (through wine). I'm looking for a way to auto-update µTorrent's ipfilter.dat

At Windows I'm using this VBS script:

> '===updater.vbs===
'
'Requires:
'
' - IE 5+ for "Microsoft.XMLHTTP"
' - ADO 2.5+ for "adodb.stream"
'
sSrcUrl = "http://mesh.dl.sourceforge.net/sourceforge/emulepawcio/"
sDestFolder = "C:\Users\Tommy\AppData\Roaming\uTorrent\"
sImageFile = "ipfilter.dat"

set oHTTP = WScript.CreateObject("Microsoft.XMLHTTP")

oHTTP.open "GET", sSrcUrl & sImageFile, False
oHTTP.send

set oStream = createobject("adodb.stream")
Const adTypeBinary = 1
Const adSaveCreateOverWrite = 2
oStream.type = adTypeBinary
oStream.open
oStream.write oHTTP.responseBody
oStream.savetofile sDestFolder & sImageFile, adSaveCreateOverWrite

set oStream = nothing
set oHTTP = nothing


Any idea how to solve this at my Ubuntu desktop?

---

### Post by lovinglinux on 2008-11-13
Try this script:

```
#!/bin/bash

wget --timeout=30 --tries=3 --timestamping --no-directories -O ~/.wine/drive_c/Users/Tommy/AppData/Roaming/uTorrent/ipfilter.dat http://mesh.dl.sourceforge.net/sourceforge/emulepawcio/ipfilter.dat
```

Save it in your personal script folder, change it's permission to run as application and then create a cron job to run it automatically.

Why do you use a proprietary windows software under wine while you have excellent native Linux alternatives? Have you tried Deluge? 

I also recommend using [[COLOR="DarkRed"]**moblock**[/COLOR]]("http://moblock-deb.sourceforge.net/") for system wide protection instead of uTorrent ipfilter.

You could also check these sites for blocklists:

[http://iblocklist.com/lists.php](http://iblocklist.com/lists.php)
[http://tbg.iblocklist.com/](http://tbg.iblocklist.com/)
[http://www.bluetack.co.uk/forums/](http://www.bluetack.co.uk/forums/)

---

### Post by Ledger on 2008-11-14
Thanks!

Deluge is banned from alot of torrentsites, so can't use it.

Edit: Stupid me didn't even think about cronjobs. Good and easy solution ^^

---

### Post by lovinglinux on 2008-11-14
> **Ledger said:**
> Deluge is banned from alot of torrentsites, so can't use it.

Never heard about such a ban. Do you know why?

---

### Post by -Zeus- on 2008-11-14
azureus (vuze) is also nice.

---

### Post by lovinglinux on 2008-11-14
It seems that banning reasons are not a real problem. 

[http://forum.deluge-torrent.org/viewtopic.php?f=7&t=9885](http://forum.deluge-torrent.org/viewtopic.php?f=7&t=9885)

---

### Post by Ledger on 2008-11-17
It's banned cause of lame staff... Tried to ask why it's banned but the pointed me to a other thread. Found nothing useful there really, only people talking about bugs in 0.5.x.

---

### Post by daleus on 2008-11-18
Most clients have a client spoof feature, try enable it and pick utorrent from the list, they won't know that you aren't really using utorrent.

---

### Post by Ledger on 2008-11-19
> **daleus said:**
> Most clients have a client spoof feature, try enable it and pick utorrent from the list, they won't know that you aren't really using utorrent.
Don't think Deluge got that future. I know that i can rewrite the code so i can switch client info sent to the tracker, but don't really wanna do that :P Did that once with rTorrent

---

