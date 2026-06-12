---
title: "[SOLVED] Can't use the Auto Login feature"
date: 2008-07-27
forum: General Help
---

### Post by VMC on 2008-07-27
Using the "System > Administration > Login Window > Security Tab" , I tried Enable Automatic Login. It took my login name but on reboot I still had to login.

I then tried from a Terminal this input:

```
sudo gdmsetup
```

Same result only now I get several errors messages:

> gdmsetup[5686]: GLib-CRITICAL: g_key_file_set_string: assertion `key_file != NULL' failed
gdmsetup[5686]: GLib-CRITICAL: g_key_file_to_data: assertion `key_file != NULL' failed
gdmsetup[5686]: GLib-CRITICAL: g_file_set_contents: assertion `contents != NULL || length == 0' failed
gdmsetup[5686]: GLib-CRITICAL: g_key_file_free: assertion `key_file != NULL' failed

This goes on for every action I take inside the gdmsetup.

---

### Post by VMC on 2008-07-28
I found a solution for this. There is several issues involved. One, there is a Lanchpad Bug report on [gdmsetup]("https://bugs.launchpad.net/ubuntu/+source/libgnomeui/+bug/199942"). 

I used Remastersys on an empty partition and when I rebooted and tried to change the Auto Login it fail.

 The reason it failed is a missing file 'gdm.conf-custom' at '/etc/gdm/'. When I replaced that file with a skeleton file , then 'sudo gdmsetup' worked again without any errors.

Here is where I actually found the clue to the [**The Fix**]("http://loscompanion.com/forums/index.php?topic=4546.0"). This gdmsetup error I have found all over the place. Unfortunately the topics come in many flavors.

---

