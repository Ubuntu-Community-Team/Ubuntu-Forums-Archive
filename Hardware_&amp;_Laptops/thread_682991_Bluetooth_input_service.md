---
title: "Bluetooth input service"
date: 2008-01-30
forum: Hardware &amp; Laptops
---

### Post by panicosm on 2008-01-30
Does anyone know how to restart bleutoothd-service-input from the prompt.
I want to schedule a restart every 15 minutes to solve reconnect problems with my Logitech diNovo.

Thanks

---

### Post by mjpoetic on 2008-01-31
I don't know if you found what you were looking for yet...but here you go!```
sudo /etc/init.d/bluetooth restart
```AFIAK, also the same as doing

```
sudo invoke-rc.d bluetooth restart
```

---

### Post by panicosm on 2008-02-02
Thanks,
I was looking to restart just the input services of bluetooth; what does 'Bluetooth Preferences' execute under 'Services' tap when I stop and start the input service.

Regards

---

### Post by phenest on 2008-02-15
I'm also having problems starting the Input service. I'm running Hardy alpha 4 with all the latest updates, and the problem started recently when a bluez-audio update was installed. Since then, I cannot start the input service to use my mouse, when was working perfectly before.

---

### Post by stoffe on 2008-03-23
> **panicosm said:**
> Thanks,
I was looking to restart just the input services of bluetooth; what does 'Bluetooth Preferences' execute under 'Services' tap when I stop and start the input service.

Regards

Been trying to do this also, for some reason the adapter goes to sleep when it's inactive and can't be woken automatically.

The following command works to *start* the service if it is stopped, sadly it is not stopped in that mode, and I can't find any "stop" or "deactivate" service command in the D-Bus API.

```
dbus-send --system --type=method_call --print-reply --dest=org.bluez /org/bluez org.bluez.Manager.ActivateService string:input
```

---

### Post by stoffe on 2008-03-24
Ok, thanks to D-feet, I've found how to restart the service via bluetooth. I have made a script that looks like this:

```
#!/bin/sh

dbus-send --system --type=method_call --dest=org.bluez /org/bluez/service_input org.bluez.Service.Stop

dbus-send --system --type=method_call --dest=org.bluez /org/bluez/service_input org.bluez.Service.Start

```

and made it executable. Then I've made a custom launcher that calls this script and put it in the panel. It's a laptop, so I have a built-in pin to do that with. It didn't work to just enter those lines (separated with ;) for some reason, had to make the script.

Anyhow, hope that helps.

Oh, and here's the bug: [https://bugs.launchpad.net/ubuntu/+source/bluez-utils/+bug/140668](https://bugs.launchpad.net/ubuntu/+source/bluez-utils/+bug/140668)

---

