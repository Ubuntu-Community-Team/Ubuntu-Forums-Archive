---
title: "minicom"
date: 2008-08-07
forum: General Help
---

### Post by waterrr on 2008-08-07
i've installed minicom and configured it through ```
minicom -s
``` and set it to ttyS0 and 9600 for baud rate...my question is I want to reset the configuration through minicom by using ```
reset saved-configuration
``` but am not able to type anything in minicom:confused:

---

### Post by CameO73 on 2008-08-07
I've no experience with minicom, but I'm using **cutecom**, which is a lot more userfriendly. It can be installed with Synaptic and may solve your problem.

---

### Post by HermanAB on 2008-08-07
You can debug serial comms by plugging a paper clip into a gender bender on pins 3 and 4, to link Rx to Tx.

I second Cutecom.  It works like a charm.

---

### Post by cszikszoy on 2008-08-07
GTKterm works well as well.

---

### Post by ModelM on 2008-08-07
To change the settings of minicom just start it again with the "-s" switch, change what you want, then select "save settings as dfl (default)".

When you are typing in minicom, you're not talking to minicom, but to your modem.

From within minicom, to return to the setup just press ctrl-a and then the letter o

---

