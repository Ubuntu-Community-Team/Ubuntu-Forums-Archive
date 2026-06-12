---
title: "Citrix ICA client error"
date: 2008-11-30
forum: General Help
---

### Post by Piccy on 2008-11-30
I am running 8.04 Hardy and use ICA for accessing my work apps from home. Until recently, ICA was working fine. Now when I try to start any Citrix apps I get this error.

[I]The server has disconnected.
This may because by failing to obtain a Microsoft Client Access License for a windows server or the requested window size may not be supported by this server.[/I]

Firefox 3.04
ICA client 10.6

I have tried 
```
sudo mkdir /etc/icalicense
sudo chmod a+rw /etc/icalicense/
``` 
without success. I even ran the icalicense.sh in ~/ICAClient/linuxx86/util which does this

```
if test ! -d /etc/icalicense
then
    mkdir /etc/icalicense
fi
if test ! -f /etc/icalicense/clientlicense
then
    /usr/lib/ICAClient/util/echo_cmd -l >/etc/icalicense/clientlicense
fi
chmod 444 /etc/icalicense/clientlicense
chmod 555 /etc/icalicense
```

None of these so far have worked. Any help would be really appreciated

---

### Post by butterman on 2008-12-26
I would also be interested in a solution to this problem.

---

### Post by Piccy on 2008-12-26
With a bit of fumbling I got it working.

I do not know if my fix will fix your issue but give it a try

Go to the keystore directory at
~/ICAClient/linuxx86/keystore/cacerts

I cut all the certificates out of the directory and pasted them someplace else (say a folder on the desktop)

Then I repasted them back into the keystore
~/ICAClient/linuxx86/keystore/cacerts minus the SecureServer.crt

I was then able to log in.

Please if you try it can you post back your results

"Happy new year":KS

---

