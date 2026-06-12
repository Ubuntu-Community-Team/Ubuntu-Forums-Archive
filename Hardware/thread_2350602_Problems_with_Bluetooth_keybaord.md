---
title: "Problems with Bluetooth keybaord"
date: 2017-01-25
forum: Hardware
---

### Post by demiurg on 2017-01-25
I'm having issues configuring a Bluetooth keyboard on 14.04.5. Command line (hcitool scan, hidd --connect) and the keyboard works. However, I cannot figure out which configuration files to modify to connect it on startup. Google suggests /etc/default/bluetooth or /etc/bluetooth/hcid.conf, but both are missing. I can, of course, stick it into any script, but what's the proper way?

If I run bluetooth-wizard, I get
Unknown command complete for opcode 37
And nothing works

---

### Post by demiurg on 2017-01-25
To summarize, the only thing which actually works is: 
hciconfig hci0 up
hidd --connect CC:C5:0A:21:78:4C

I can stick these lines into any random script, but why the heck there is no proper configuration file?

---

### Post by demiurg on 2017-01-25
OK, so /etc/init.d/bluetooth has this:
hci_input()
{
    log_progress_msg "switching to HID/HCI no longer done in init script, see /usr/share/doc/bluez/NEWS.Debian.gz" || :
}
alias enable_hci_input=hci_input
alias disable_hci_input=hci_input


What the heck is going on?

---

