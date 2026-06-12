---
title: "gnome-volume-manager fails to mount ieee1394 HD"
date: 2004-12-30
forum: Hardware &amp; Laptops
---

### Post by noisyjazzman on 2004-12-30
As I understand it, gnome-volume-manager should just mount an external firewire drive without my intervention (have I got this right?).

On my Ubuntu (warty) installation, it doesn't. /var/log/messages shows the device being detected, and I can manually mount the drive OK.

However, if I run pmount /dev/sda1 once, from that point on the automounting does work (ie. I run pmount, the HD icon appears on the desktop, I unmount it from the context menu, switch the drive on again, and this time it does automount). This works until the next reboot, after which I have to manually run pmount again.

As a result I have a couple of questions:

- how can I troubleshoot the cause of this issue?
- does anyone know of any resources where I can read about how gnome-volume-manager works and is configured? I really feel I'm flying blind. There is a readme in /usr/share/doc/gnome-volume-manager, but that directly contradicts other advice I've seen, in that it claims you do need an fstab entry for removable devices.

---

### Post by noisyjazzman on 2004-12-31
Have I submitted this to the wrong forum?

---

### Post by xkcdmagic8 on 2004-12-31
im not sure about how to solve ur problem but i think most arnt sure or they're too lazy to answer :P Just wait i think..

---

### Post by noisyjazzman on 2005-01-02
[QUOTE=nitinshantharam]im not sure about how to solve ur problem but i think most arnt sure or they're too lazy to answer :P Just wait i think..[/QUOTE]
 Actually I asked about the forum because I wondered if I had offended in some way or abused some forum etiquette. Linux people always claim that the 'difficulties' of linux don't really matter as newbies can easily get advice from all the 'friendly' mailing lists and fora. But that just isn't my experience. I try Linux for a while, hit some problem that I can't fix even after hours of reading, so then post questions which no-one answers (I've been through this with Mandrake, Fedora, and now Ubuntu). Hence I never really get things working as I want them.

Admittedly I'd probably get answers if I asked 'how do I add menu items ' or some other trivial question, but with anything more difficult I have to just find the answer myself or forget about.

---

### Post by bitserf on 2005-01-02
hi,

i'm not entirely sure about this either, documentation sucks somewhat, IEEE1394 automounting is pretty flaky for me too.

sometimes it would mount it, sometimes not. sometimes it would mount it, and open up a nautilus window, but not create an icon on the desktop.

make sure you have "true" as the value for <storage_automount_enabled_hint> in /etc/hal/hald.conf, and that gnome-volume-properties says to "Mount removable drives when hot-plugged" and "Mount removable media when inserted" (though the difference between the two is totally unclear from that text), I'm not sure either. 

i wish they wouldn't invent terminology, or at least have decent context help for dialogs. confuses even expert users.

anyhow, i also did an additional tweak to /etc/hal/fdi/preferences.fdi:

 <device>
    <match key="block.is_volume" bool="true">
      <match key="@block.storage_device:storage.model" string="iPod">
        <merge key="volume.policy.mount_option.uid=1000" type="bool">true</merge>
        <merge key="volume.policy.desired_mount_point" type="string">ipod</merge>
        <merge key="volume.label" type="string">iPod</merge>
      </match>
    </match>
  </device>

this mounts it as me, always (evil probably, there's probably a better way to do this), always mounts it on /media/ipod (it used to use random mountpoints before that), and makes the volume label "iPod".

but yeah...there are so many movable parts in Project Utopia (heh), it can make it difficult to debug :)

---

### Post by noisyjazzman on 2005-01-06
[QUOTE=bitserf]hi,

i'm not entirely sure about this either, documentation sucks somewhat, IEEE1394 automounting is pretty flaky for me too.

sometimes it would mount it, sometimes not. sometimes it would mount it, and open up a nautilus window, but not create an icon on the desktop.

make sure you have "true" as the value for <storage_automount_enabled_hint> in /etc/hal/hald.conf, and that gnome-volume-properties says to "Mount removable drives when hot-plugged" and "Mount removable media when inserted" (though the difference between the two is totally unclear from that text), I'm not sure either. 

i wish they wouldn't invent terminology, or at least have decent context help for dialogs. confuses even expert users.

anyhow, i also did an additional tweak to /etc/hal/fdi/preferences.fdi:

 <device>
    <match key="block.is_volume" bool="true">
      <match key="@block.storage_device:storage.model" string="iPod">
        <merge key="volume.policy.mount_option.uid=1000" type="bool">true</merge>
        <merge key="volume.policy.desired_mount_point" type="string">ipod</merge>
        <merge key="volume.label" type="string">iPod</merge>
      </match>
    </match>
  </device>

this mounts it as me, always (evil probably, there's probably a better way to do this), always mounts it on /media/ipod (it used to use random mountpoints before that), and makes the volume label "iPod".

but yeah...there are so many movable parts in Project Utopia (heh), it can make it difficult to debug :)[/QUOTE]
 Thanks for the suggestions. I haven't got it working yet, but I've learnt a bit more by following those up and reading the hal config files.

It's a bit frustrating, as the lack of documentation means that I still have no idea whether this represents a bug or not, hence whether or not to log it as such. 

If anyone knows where I might find more information, I'd still be interested to hear.

---

### Post by ghostwind on 2005-01-06
Hi if you want a distro that mounts ok try 
[http://www.xandros.com/products/home/desktopoc/dsk_oc_download.html](http://www.xandros.com/products/home/desktopoc/dsk_oc_download.html)

I want ubunto to mount just as good if not better than Xandros.

Cheers

Colin :D

---

### Post by cacofonix on 2005-01-06
[QUOTE=noisyjazzman]Actually I asked about the forum because I wondered if I had offended in some way or abused some forum etiquette. Linux people always claim that the 'difficulties' of linux don't really matter as newbies can easily get advice from all the 'friendly' mailing lists and fora. But that just isn't my experience. I try Linux for a while, hit some problem that I can't fix even after hours of reading, so then post questions which no-one answers (I've been through this with Mandrake, Fedora, and now Ubuntu). Hence I never really get things working as I want them.

Admittedly I'd probably get answers if I asked 'how do I add menu items ' or some other trivial question, but with anything more difficult I have to just find the answer myself or forget about.[/QUOTE]

From reading through countless forums if you were to ask how to add menus you would more than likely  get flamed for not searching the forums or told to RTFM or even ignored completely :(.

I don't know how to fix your problem NJM I have a work around, what about creating a launcher on your desktop that you just need to double click on it when gnome won't mount your drive automatically?

cacofonix

---

### Post by noisyjazzman on 2005-01-06
[QUOTE=cacofonix]From reading through countless forums if you were to ask how to add menus you would more than likely  get flamed for not searching the forums or told to RTFM or even ignored completely :(.

I don't know how to fix your problem NJM I have a work around, what about creating a launcher on your desktop that you just need to double click on it when gnome won't mount your drive automatically?

cacofonix[/QUOTE]
 That's a possibility, though ideally I'd like the drive to mount without intervention, even when no-one's logged in. I'm also looking into using automount as an alternative to  gnome-volume-manager.

---

### Post by wallijonn on 2005-01-06
[QUOTE=noisyjazzman] This works until the next reboot, after which I have to manually run pmount again.[/QUOTE]

What about adding the device in /etc/modules?

---

### Post by cacofonix on 2005-01-06
Seeing your having trouble with hot plugging the ubunutuwiki has what the developers want you to do so they can improve hot plugging support:

[wiki firewire](http://www.ubuntulinux.org/wiki/FrequentlyAskedQuestions#usbfirewire)


cacofonix

---

