---
title: "Sync with Barry"
date: 2009-04-01
forum: Hardware
---

### Post by wbryan6 on 2009-04-01
I have spent all day trying to setup my laptop to sync my blackberry with Evolution, and I'm almost there.  After following all of the steps on "http://www.netdirect.ca/software/packages/barry/sync.php", I hit a snag.  When I try to setup the sync groups and I type "msynctool --addmember EvoBarry barry-sync", I get the following message:
```
Unable to instance plugin with name barry-sync: Unable to find the plugin "barry-sync"
```
I found another post that said something about there not being a barry-sync file in /usr/share/opensync/defaults, so I copied evo2-sync to barry-sync, but that didn't help.  I've come to the realization that barry-sync is a plugin for opensync that I need to install.  I read everything I could find on their website ([http://www.opensync.org](http://www.opensync.org)), but to no avail.  Anyone else have additional input?  Thanks in advance.

---

### Post by version7x on 2009-04-05
I dont know if this will help, but I have a barry-sync file, but no evo2-sync file...

My barry-sync file is located in:
/usr/local/share/opensync/defaults

And it looks like so....

```
#
# This is the default configuration file for the barry-sync opensync plugin.
# Comments are preceded by a '#' mark at the beginning of a line.
# The config format is a set of lines of <keyword> <values>.
#
# Keywords available:
#
# DebugMode        - If present, verbose USB debug output will be enabled
#
# Device           - If present, it is followed by the following values:
#      PIN number    - PIN number of the device to sync with (in hex)
#      sync calendar - 1 to sync calendar, 0 to skip
#      sync contacts - 1 to sync contacts, 0 to skip
#
# Password secret  - If present, specifies the device's password in plaintext
#

#DebugMode

Device ........ 1 1

#Password secret

```

So the only thing in mine is the Device declaration... which I've removed the value of above.  Everything else is commented out.  Since I can't get mine to work either, I don't know if this will help~

What does your evo2-sync file look like?

---

### Post by wbryan6 on 2009-04-06
Now this is a little strange.  After my last post, I downloaded new barry files from another site and installed those. With these new files, I was still getting the same message when trying to setup the msynctool groups.  I assumed it was still exactly the same problem, but now when I look in /usr/share/opensync/defaults there is a barry-sync file that looks exactly like the text you posted.  However, when I run msynctool --listplugins, all I get is (still):

```
Available plugins:
evo2-sync

```

version7x, if you run this listplugins command, does it show barry-sync??  I even tried changing the perms, ownership, and group but to no avail.  Here is what my evo2-sync file looks like:

```
<config>
  <address_path>default</address_path>
  <calendar_path>default</calendar_path>
  <tasks_path>default</tasks_path>
</config>

```

Thanks for the response.  Hopefully someone out there has dealt with this before.

---

### Post by version7x on 2009-04-07
However, when I run msynctool --listplugins, all I get is (still):

```
Available plugins:
evo2-sync

```

version7x, if you run this listplugins command, does it show barry-sync??  I even tried changing the perms, ownership, and group but to no avail. 

Thanks for the response.  Hopefully someone out there has dealt with this before.[/QUOTE]

This is really odd....  here's mine:

```
$msynctool --listplugins
Available plugins:
barry-sync

```

I've been trying to install the evo2-plugin manually, but am hitting roadblocks there too.  All I've installed is the libopensync, msynctool, and barry tarballs... along with the list of prereqs [here...]("http://ubuntuforums.org/showthread.php?t=854716")

I'm pretty stuck at this point and I'm not sure what we've done that's lead to such different (crappy) outcomes!

---

### Post by dreperk on 2009-04-28
If you have MultiSync installed, use the GUI to delete your group.  Then go to terminal and recreate your group and it's members from scratch.  This helped me when I tried to configure barry-sync and got a blank config file.  Not sure if this will help, but a shot in the dark I guess.  Good luck.

EDIT:  As a side, everything "Barry" and "Opensync" is included in the default repos in Jaunty.  If you have upgraded this will prevent you from having to search hither and yon for all of the required packages.

---

### Post by version7x on 2009-05-02
> **dreperk said:**
> As a side, everything "Barry" and "Opensync" is included in the default repos in Jaunty.  If you have upgraded this will prevent you from having to search hither and yon for all of the required packages.

I've now upgraded to Jaunty... still no luck with Barry... it doesnt see my phone at all, but at least I dont have to worry about all of the plugin issues.  I've also intalled multisync.  I'll play around with that this week.

Thanks!

---

### Post by rommer on 2009-05-07
No matter what I do when I list the plugins barry-sync does not show up.

Not sure what else to try.

# msynctool --listplugins
Available plugins:
evo2-sync

# ls -l /usr/share/opensync/defaults/
total 8
-rw-r--r-- 1 root root 691 2009-05-07 11:18 barry-sync
-rw-r--r-- 1 root root 134 2008-08-07 00:53 evo2-sync

---

