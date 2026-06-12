---
title: "Sony Clie  SJ22"
date: 2010-01-25
forum: Hardware
---

### Post by donniesito on 2010-01-25
Hi all
    I am currently dual-booting between Win7 x64 and Ubuntu 9.10 (also 64 bit).
    I am looking for a way to be able to sync with and install software to my Sony Clie SJ22 within Ubuntu. I have tried setting up with "Palm OS Devices" with no luck; it said the visor module wasn't loaded.
    SO -- I did "sudo modprobe visor" then reran "Palm OS Devices."  Now when I press the sync button on the Clie, I get a fatal exception error and have to reset it (the palm).
    Any suggestions?

---

### Post by ka1ssr on 2010-02-19
I'm having the same problem with my SJ22.  Everything was working fine under 9.04 but things broke with the upgrade to 9.10.  Pressing the HotSync button on the PDA and executing lsusb shows that the PC is seeing the PDA.  gpilotd is running.  I've tried various interface combinations in the gnome pilot panel.  USB always worked in the past.

I posted this issue on Launchpad a month ago but the question never got a response.  I've seen it mentioned on other versions of Ubuntu on Launchpad.  Never could figure out if it was finally resolved.  It would be great if someone in the know could post a response.

I miss my HotSync!

Bill

---

### Post by ka1ssr on 2010-02-19
More helpful info.

I killed gpilotd and ran it in a terminal window.  Here are the messages I got.  Items in brackets are my notes.

```
ka1ssr@ernie:~/audacity$ gpilotd &
[1] 4053
ka1ssr@ernie:~/audacity$ gpilotd-Message: gnome-pilot 2.0.17 starting...
gpilotd-Message: compiled for pilot-link version 0.12.3
gpilotd-Message: compiled with [VFS] [USB] [IrDA] [Network] [Bluetooth] 
gpilotd-Message: Activating CORBA server
gpilotd-Message: bonobo_activation_active_server_register = 0
gpilotd-Message: Watching Cable (usb:)
gpilotd-Message: Found 4766, 0001
gpilotd-Message: Using net TRUE
gpilotd-Message: Found 0502, 0736
gpilotd-Message: Using net TRUE
gpilotd-Message: Found 091e, 0004
gpilotd-Message: Using net TRUE
gpilotd-Message: Found 115e, f100
gpilotd-Message: Using net TRUE
gpilotd-Message: Found 082d, 0100
gpilotd-Message: Using net FALSE
gpilotd-Message: Found 082d, 0200
gpilotd-Message: Using net TRUE
gpilotd-Message: Found 082d, 0300
gpilotd-Message: Using net TRUE
gpilotd-Message: Found 0c88, 0021
gpilotd-Message: Using net TRUE
gpilotd-Message: Found 0830, 0001
gpilotd-Message: Using net TRUE
gpilotd-Message: Found 0830, 0002
gpilotd-Message: Using net TRUE
gpilotd-Message: Found 0830, 0003
gpilotd-Message: Using net TRUE
gpilotd-Message: Found 0830, 0020
gpilotd-Message: Using net TRUE
gpilotd-Message: Found 0830, 0031
gpilotd-Message: Using net TRUE
gpilotd-Message: Found 0830, 0040
gpilotd-Message: Using net TRUE
gpilotd-Message: Found 0830, 0050
gpilotd-Message: Using net TRUE
gpilotd-Message: Found 0830, 0060
gpilotd-Message: Using net TRUE
gpilotd-Message: Found 0830, 0061
gpilotd-Message: Using net TRUE
gpilotd-Message: Found 0830, 0070
gpilotd-Message: Using net TRUE
gpilotd-Message: Found 0830, 0080
gpilotd-Message: Using net TRUE
gpilotd-Message: Found 04e8, 8001
gpilotd-Message: Using net TRUE
gpilotd-Message: Found 04e8, 6601
gpilotd-Message: Using net TRUE
gpilotd-Message: Found 054c, 0038
gpilotd-Message: Using net TRUE
gpilotd-Message: Found 054c, 0066
gpilotd-Message: Using net TRUE
gpilotd-Message: Found 054c, 0095
gpilotd-Message: Using net TRUE
gpilotd-Message: Found 054c, 009a
gpilotd-Message: Using net TRUE
gpilotd-Message: Found 054c, 00c9
gpilotd-Message: Using net TRUE
gpilotd-Message: Found 054c, 00da
gpilotd-Message: Using net TRUE
gpilotd-Message: Found 054c, 00e9
gpilotd-Message: Using net TRUE
gpilotd-Message: Found 054c, 0144
gpilotd-Message: Using net TRUE
gpilotd-Message: Found 054c, 0169
gpilotd-Message: Using net TRUE
gpilotd-Message: Found 12ef, 0100
gpilotd-Message: Using net TRUE
gpilotd-Message: setting PILOTRATE=57600

[longish pause]

(gpilotd:4053): gpilotd-WARNING **: An error occurred while getting the PDA's system data

(gpilotd:4053): gpilotd-WARNING **: error -201 from pi_close.

[Clie gives up and times out]

```

Any developers out there who can help?

Thanks!

Bill

---

### Post by ka1ssr on 2010-05-10
Happy ending.  I upgraded to 10.04 and I can sync again!

Bill

---

