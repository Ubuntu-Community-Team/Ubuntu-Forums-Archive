---
title: "ubuntu wont boot, can't load udev.conf"
date: 2008-07-19
forum: General Help
---

### Post by 4140 on 2008-07-19
Hi,

I am using ubuntu for 2 months and I had no problems till 2 days ago, when after instaling the updates and making the required reboot my system doesn't want to boot. It says, that can't load udev.conf.

Now I am runing the recovery mode from the day befor the crash and don't know what to do.

[EDIT]

I've reinstalled udev using synaptic and reboot trough terminal (it couldn't do it by cliking the button :)) and it seems workin' now

Cheers!

---

### Post by RealPSL on 2008-07-19
I am not sure this will help but if you can get to the /etc/udev directory in recovery mode you can recreate the file. I really just has 1 meaningful line in there. If it already exists back it up and then overwrite it with ```
echo "udev_log="err" > /etc/udev/udev.conf
```. Or use an editor like nano to put it back.

---

