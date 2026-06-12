---
title: "[SOLVED] Network Manager - hangs shutdown"
date: 2008-10-18
forum: General Help
---

### Post by spiperman on 2008-10-18
Hi all - I'm new to ubuntu (v 7.10) and have been searching to fix a network manager error that consistently appears during shutdown.  The error is as follows - 

nm_dbus_signal_device_status_chg: assertion 'cb-data -> data -> dbus_connection' failed

Once the shutdown process reaches this error - a manual power off is required and I have no idea of what is not being completed.

I've done some reading and found several suggestions about disabling NM but that seems to negatively impact having eth0 set for dhcp. I have disabled the Bluetooh service - I have no need for that.

I upgraded to 8.04 but that caused more problems so I just reinstalled 7.10  and started over again. I've got enough time invested in the configuration of the machine where I really don't want to do that again.

If it matters, the platform is a AMD 5400+ w/1GB RAM on a via micro ATX MB, ATI 9400 graphics card. With the exception ofthe graphics card, everything is built into the MB.

Any ideas would be welcome.

Cheers,
 
Sam

---

### Post by spiperman on 2008-10-19
A solution has been found...it's been working today anyway so I think it's a good one.

After installing (well actually reinstalling) the LAMP stack I got a new error 

"nm_hal_deinit(): libhal shutdown failed - connection is closed"

This lead me back to Launchpad and there I found this response:

[https://answers.launchpad.net/ubuntu/+question/16914](https://answers.launchpad.net/ubuntu/+question/16914)

that addresses both messages.  So - today is a good day.

Cheers, 

Sam

---

