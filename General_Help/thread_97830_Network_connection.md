---
title: "Network connection"
date: 2005-12-01
forum: General Help
---

### Post by canadianwriterman on 2005-12-01
Here's my situation and I hope someone has some ideas. Yesterday, my DSL connection to the Internet (Web browser, e-mail, Synaptic, etc.) would not work in both Ubuntu and Windows. In Windows, it would only work if I deleted my Broadband connection and created a new one. However, I lost the connection everytime I rebooted. In Linux, I couldn't figure out how to create a new Broadband connection, so I left it for the time being.

I read a forum post that recommended unplugging the modem for 5 minutes and then letting it reset. That seems to have worked. The problem now is that I have to manually connect each time I reboot. In Windows, I have to right click on the Broadband icon in Control panel and click connect. In Ubuntu, I have to open **System > Administration > Networking**, click on eth0 and activate it. Previously, the connection was automatic on boot up in both Windows and Ubuntu. 

My question is, is there any setting I can use to have my eth0 connection activate automatically on boot up?

---

### Post by kairu0 on 2005-12-01
Maybe you aren't allowing enough time for the modem to authenticate itself with your DHCP provider before you turn on your computer.

You can verify this by checking for a long delay during the network initialization stage of the boot.

---

### Post by canadianwriterman on 2005-12-01
[QUOTE=kairu0]Maybe you aren't allowing enough time for the modem to authenticate itself with your DHCP provider before you turn on your computer.

You can verify this by checking for a long delay during the network initialization stage of the boot.[/QUOTE]

There isn't any abnormal delay in network initialization during bootup. This is only just a brand new behaviour. Prior to yesterday, the network connection was always up and running in both Windows and Ubuntu when the boot up was complete. Now, they both have to be connected manually. It's almost like there is a setting to "connect eth0 automatically on bootup" that isn't set.

---

### Post by RAOF on 2005-12-01
[QUOTE=canadianwriterman]...It's almost like there is a setting to "connect eth0 automatically on bootup" that isn't set.[/QUOTE]
Actually, there **is** a setting "connect on startup" in the network config.  That's presumably checked? ;)

---

