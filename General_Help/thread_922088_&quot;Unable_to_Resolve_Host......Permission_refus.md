---
title: "&quot;Unable to Resolve Host......Permission refused"
date: 2008-09-16
forum: General Help
---

### Post by chhmelb on 2008-09-16
I installed Hardy Heron on Advent 4211B (? = MSI Wind).   (Ubuntu 8.04.1  Kernel 2.6.24-19 generic)
Naturally, the Wifi doesn't work out of the box, nor so far with ndiswrapper, although it has slowed down the system response.

However, while trying to diagnose/correct these issues, I have needed to run commands prefixed by sudo. My Terminal window prompt is
          chh@ubuntuchh:~$        (my logon is chh)

and when I run any command prefixed by sudo I get the usual 1-2 min pause before any program is run, then:

          unable to resolve host ubuntuchh  

I looked up fixes for this and tried to follow a suggestion to resolve this by amending the /etc/hosts file.  However, on trying to save the file I get:  

"Could not save file: You do not have the necessary permissions"

Trying to log on as "root", I get 

"The system administrator is not allowed to log on from this screen".

Is there any way a system administrator can administrate in Hardy Heron?  Is this a problem with ndiswrapper?

Any help gratefully accepted.

---

### Post by iaculallad on 2008-09-16
You have to have the privilege to save whatever you edited on your /etc/hosts file. To do this:

```
gksudo gedit /etc/hosts
```

This will ask for password, input your OWN user password, append all the changes you want on the file and save it.

By default, you cannot login as root as in **su** command as Ubuntu disabled it. You can however use:

```
sudo -i
```

```
sudo -s
```

or

```
sudo su
```

to get in a 'root-like' privilege.

---

### Post by zvacet on 2008-09-17
If you can not use sudo boot in recovery mode and type

```
nano /etc/hosts
```

First two line should look like 

> 127.0.0.1 localhost
127.0.1.1 **yourusername**

If your lines doesn´t look like that make it so.Close file and exit.Reboot and see if it works.

---

### Post by plucky on 2008-09-17
@zvacet

> 127.0.0.1 localhost
[color=red]127.0.1.1 yourusername[/color]


Shouldn't that read as **yourhostname**

---

### Post by chhmelb on 2008-09-17
Many thanks to iaculallad and zvacet.  When I tried gedit, I realised that I still have to learn to use all these tools: <ctrl>z don't work like it did in DOS!  Will do more background reading before checking these 3 methods out.  Meanwhile I found an easier (for ignorant s***s like me) way of solving the problem from Serenity ([https://bugs.launchpad.net/...):](https://bugs.launchpad.net/...):)

"go to the System Control Panel in the GUI:
"->Admin   -->Network   ---> UNLOCK   ----General: Remove Domain Name
"Go to Hosts (Under Network) - delete 127.0.1.1
"Add 127.0.1.1
"Add Hostname only, no domain entry
This worked like a charm - including preventing those 2-3 minute system hangs - and showed that the hosts file had somehow been corrupted by settings imported from my router.  Whether this was done through the wireless card (which was otherwise non-functional) or the wired connection remains a mystery, but since the problem only surfaced after ndiswrapper, it must have something to do with that.

Thanks again everyone - and I'll do more homework before asking the next daft question!

---

