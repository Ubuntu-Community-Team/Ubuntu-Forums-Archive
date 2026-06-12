---
title: "USB drives not automounting, possible solution!"
date: 2008-07-12
forum: General Help
---

### Post by MattK358 on 2008-07-12
After running in to several walls and skimming countless threads on this problem I think I found a solution!

Running an up to date install of Hardy, with GNOME my USB drives would not mount properly. They would show up in places, work from the command line etc but the automount just wasn't going to work. So a little bit of sniffing and I tried to use the gnome-mount command and came up with this:

```

matt@Godzilla:~$ gnome-mount -vbd /dev/sdb1
gnome-mount 0.8
** (gnome-mount:30183): DEBUG: Mounting /org/freedesktop/Hal/devices/volume_uuid_4EF4_3A8A
** (gnome-mount:30183): DEBUG: read default option 'utf8' from gconf strlist key /system/storage/default_options/vfat/mount_options
** (gnome-mount:30183): DEBUG: read default option 'umask=077' from gconf strlist key /system/storage/default_options/vfat/mount_options
** (gnome-mount:30183): DEBUG: read default option 'exec' from gconf strlist key /system/storage/default_options/vfat/mount_options
** (gnome-mount:30183): DEBUG: read default option 'flush' from gconf strlist key /system/storage/default_options/vfat/mount_options
** (gnome-mount:30183): DEBUG: Mounting /org/freedesktop/Hal/devices/volume_uuid_4EF4_3A8A with mount_point='KRASS', fstype='', num_options=4
** (gnome-mount:30183): DEBUG:   option='shortname=mixed'
** (gnome-mount:30183): DEBUG:   option='uid=1000'
** (gnome-mount:30183): DEBUG:   option='utf8'
** (gnome-mount:30183): DEBUG:   option='umask=077'
** (gnome-mount:30183): DEBUG:   option='exec'
** (gnome-mount:30183): DEBUG:   option='flush'
** Message: Mount failed for /org/freedesktop/Hal/devices/volume_uuid_4EF4_3A8A
org.freedesktop.Hal.Device.PermissionDeniedByPolicy : org.freedesktop.hal.storage.mount-removable no <-- (action, result)

** (gnome-mount:30183): DEBUG: pk_action='org.freedesktop.hal.storage.mount-removable' pk_result='no'
** (gnome-mount:30183): DEBUG: gained privilege = 0
matt@Godzilla:~$ 

```

A bit of googling turned up this:
[http://cblfs.cross-lfs.org/index.php/PolicyKit](http://cblfs.cross-lfs.org/index.php/PolicyKit)

At the bottom in the Configuration heading is a solution, just make the required changes to the PolicyKit file and restart hald:
```

matt@Godzilla:/etc/PolicyKit$ sudo /etc/init.d/hal restart
 * Restarting Hardware abstraction layer hald                                                                                                                             [ OK ] 
matt@Godzilla:/etc/PolicyKit$ gnome-mount -vbd /dev/sdb1
gnome-mount 0.8
** (gnome-mount:30260): DEBUG: Mounting /org/freedesktop/Hal/devices/volume_uuid_4EF4_3A8A
** (gnome-mount:30260): DEBUG: read default option 'utf8' from gconf strlist key /system/storage/default_options/vfat/mount_options
** (gnome-mount:30260): DEBUG: read default option 'umask=077' from gconf strlist key /system/storage/default_options/vfat/mount_options
** (gnome-mount:30260): DEBUG: read default option 'exec' from gconf strlist key /system/storage/default_options/vfat/mount_options
** (gnome-mount:30260): DEBUG: read default option 'flush' from gconf strlist key /system/storage/default_options/vfat/mount_options
** (gnome-mount:30260): DEBUG: Mounting /org/freedesktop/Hal/devices/volume_uuid_4EF4_3A8A with mount_point='KRASS', fstype='', num_options=4
** (gnome-mount:30183): DEBUG:   option='shortname=mixed'
** (gnome-mount:30183): DEBUG:   option='uid=1000'
** (gnome-mount:30260): DEBUG:   option='utf8'
** (gnome-mount:30260): DEBUG:   option='umask=077'
** (gnome-mount:30260): DEBUG:   option='exec'
** (gnome-mount:30260): DEBUG:   option='flush'
Mounted /dev/sdb1 at "/media/KRASS"
matt@Godzilla:/etc/PolicyKit$ 

```

And you should all up and running!

Hope this helps someone.

---

### Post by sped44 on 2008-07-30
Thanks man, that helped me fix a very annoying problem.

Shawn

---

### Post by c-m on 2008-09-22
My camera, 3 usb sticks and two mobile phones do not mount automatically. They did before I updated to Ubuntu 8.04

Can some expain the fix above please, I'm not sure what PolicyKit is or what I need to change.

---

### Post by sicofante on 2008-09-22
I don't understand this fix either. I just executed the commands in the second code textbox, the pendrive got mounted. Then I unmounted it, extracted it and plugged it back again. No automount. :(

---

### Post by mc4man on 2008-09-22
The 'fix', if that's what it turns out to be, is at the bottom of the linked page. I would read the whole paragraph. Personally I wouldn't use it unless one was willing to deal with unexpected results should they occur.

While you shouldn't have to do this and it may have no effect, you could try this, ( no harm possible

Go to system -> administration -> authorizations. Scroll down to volumes and choose 'mount file systems from removable drives'. In the box click 'grant', from the drop down in 'select user' choose your username.

---

### Post by c-m on 2008-09-22
already did that off my own bat when looking around my system for a fix. it did not work, which is why i came online for a solution.

the linked page to me is just a wiki page with history about something called PolicyKit

---

### Post by mc4man on 2008-09-22
>  Configuration

To allow HAL to automount removable drives such a thumbdrives, edit /etc/PolicyKit/PolicyKit.conf and add the following between the <config></config> tags:

<match action="org.freedesktop.hal.storage.mount-removable">
    <return result="yes" />
</match>

Without this you will receive an error similar to org.freedesktop.Hal.Device.PermissionDeniedByPolicy: org.freedesktop.hal.storage.mount-removable no <--(action,result) when you "plug in" your thumb drive.

You then must upgrade your util-linux to the latest version or HAL automounting will fail with the following error FAT: Unrecognized mount option "uhelper=hal" or missing value. Instructions for building the latest version of util-linux can be found the development CLFS books.
```

<match action="org.freedesktop.hal.storage.mount-removable">
    <return result="yes" />
</match>

```


To view your current file
```
gedit /etc/PolicyKit/PolicyKit.conf
```

to edit use 
```
gksudo gedit /etc/PolicyKit/PolicyKit.conf
```

Note the formatting when using quote tags changes things a little, hence the code box or refer to link.

---

### Post by sp200606 on 2008-11-11
Thanks, editing the "System | Administration | Authorisations" (sudo polkit-gnome-authorization in terminal mode) does the trick fine. The changes are effective right away, no need to restart any service...

---

### Post by Paulmoore on 2008-11-19
Hmm. neither solution worked for me. It seems like a lot of people are having this problem on Intrepid. Anyone else have any ideas?

---

### Post by Bobby 'Buntu on 2009-02-02
I had this problem and found the cause was in /etc/hal/fdi/policy/gparted-disable-automount.fdi

This was telling hal to not automount any hot-pluggable drives, which unfortunately meant USB thumb drives would not get mounted.

Editing the file to allow automounting of removable drives (while still preventing automounting of non-removable, hotpluggable drives) solved things for me.

```

<deviceinfo version='0.2'>
  <device>
    <match key='storage.hotpluggable' bool='true'>
      <match key='storage.removable' bool='false'>
        <merge key='storage.automount_enabled_hint' type='bool'>false</merge>
      </match>
    </match>
  </device>
</deviceinfo>

```

Hal needed a restart after editing the file for this change to be picked up.

```

sudo /etc/init.d/hal restart

```

---

### Post by YesSir on 2009-02-03
I encounter the same problem.. Automount and unmount do not work properly. In my case, mounting usb drives only works when I connect them *before* starting the computer. 

Also, when a drive is mounted, ubuntu will not shut down properly. Anyone recognises these problems? Will try your solutions, when I get home ;)

---

### Post by xinman on 2009-02-06
I am having the same problem, none of my jump drives work on 8.04.  I have an old box running 5..10 that doesn't have any trouble.  This is finally my attempt at going linux as the primary desktop and between the jump drives, sd cards, blackberry, and video camera I'm having a hell of a time.  I did however get my printer working just now so, woot!  Back to the subject any other ideas to get mounting working would be great, at this point I can't even get it to mount manually.  Ideas?

---

### Post by usererror on 2009-12-15
To the Original Poster:

THANK YOU! This fixed my HAL problem. I'm running xubuntu on server and this worked perfectly!

---

### Post by ntlam on 2010-01-21
> **mc4man said:**
> ```

<match action="org.freedesktop.hal.storage.mount-removable">
    <return result="yes" />
</match>

```


To view your current file
```
gedit /etc/PolicyKit/PolicyKit.conf
```

to edit use 
```
gksudo gedit /etc/PolicyKit/PolicyKit.conf
```

Note the formatting when using quote tags changes things a little, hence the code box or refer to link.

This works for me. Thanks a lot.

Lam

---

### Post by startling on 2010-01-28
I don't know if it's helpful or not but I had a problem where Ubuntu wasn't automounting my USB drive so instead I went to Places > Computer and it showed up there. I clicked on its icon and it gave me an error message saying "unable to mount location" but it went and mounted it anyway!

(I don't know it had any bearing on this solution but I had restarted the HAL before going to Places > Computer.)

---

### Post by 73ChargerFan on 2010-01-28
My karmic laptop stopped automounting today, and I received unknown hal / freedesktop errors in pcmanfm.  My fault, though - I had removed the ntfs-3g package, but forgot that my usb memory sticks were formatted that way.  Reinstalling fixed it in a jiffy.

---

