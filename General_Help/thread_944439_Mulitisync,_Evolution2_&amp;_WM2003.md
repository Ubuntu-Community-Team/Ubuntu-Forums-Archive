---
title: "Mulitisync, Evolution2 &amp; WM2003"
date: 2008-10-11
forum: General Help
---

### Post by Steve H on 2008-10-11
Does anyone know what this error message means? I get it when running Multisync:
```

multisync
plugin_API_version
short_name
long_name
plugin_init
always_connected
[evo2-sync] DEBUG: start: sync_connect
[evo2-sync] INFORMATION: Loading state from file /home/*******/.multisync/7/localsettings
[evo2-sync] DEBUG: end: load_palm_state
[evo2-sync] DEBUG: end: sync_connect
** Message: Hal reports no devices connected

** (multisync:26146): WARNING **: synce_info_from_odccm: Failed to get devices: The name org.synce.odccm was not provided by any .service files
[rra_contact_to_vcard2:969] Did not handle field with ID fffd
[rra_contact_to_vcard2:969] Did not handle field with ID fffe
[rra_contact_to_vcard2:969] Did not handle field with ID fffd
[rra_contact_to_vcard2:969] Did not handle field with ID fffe
[rra_contact_to_vcard2:969] Did not handle field with ID fffd
[rra_contact_to_vcard2:969] Did not handle field with ID fffe
Segmentation fau
```lt

I've noticed a few people having this problem, but no surefire solutions. I can sync my calendar between the ipaq and Evolution2 but nothing else syncs (notes, tasks etc).

I use a little bash script to run the commands, which allows me to mount and browse the files on the ipaq (synce:/// in nautilus). So it is all connecting it just doesn't seem to like syncing anything other than the calendar.

Has anyone got any tips on getting rid of this segemntation fault on multisync 0.8??

--------------------------------------------------------------------------
EDIT:
Ok, so I've got a bit further. I'm now able to get Multisync to stand up and sync without error using Multisync0.90 and the Windows CE plug-in for Intrepid ( abit of gaffer tape and string holding it together).

Now at at least I'm not getting any segmentation faults during a sync cycle. Now I just need to work out how to get it to sync the contacts, tasks, etc. It is syncing the calendar but not contacts, task etc although it does look like it does, but they are not showing up in Evolution

Anyone got any ideas?
Anyone?
Anyone?
Bueller?

---

