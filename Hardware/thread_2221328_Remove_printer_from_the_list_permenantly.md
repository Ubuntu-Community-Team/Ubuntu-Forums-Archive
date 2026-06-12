---
title: "Remove printer from the list permenantly"
date: 2014-05-01
forum: Hardware
---

### Post by Rgc183 on 2014-05-01
I want to remove some printers which I see in system settings->printers section. I edited the file /etc/cups/printer.conf and it removes it temporarily, but when I reboot the machine it seems that it adds the printers automatically from the network. How can I avoid this/ remove them permanently?
I tried with sudo lpadmin -x  as well.

---

### Post by Morbius1 on 2014-05-01
The ability of cups to detect and create a local print queues of remote printers is made possible by a utility called cups-browsed.

If you disable the service you should see all the remote printers detected this way disappear - after a while:
```
sudo service cups-browsed stop
```
To make it permanent one way is to rename the service config file so it won't run:
```
sudo mv /etc/init/cups-browsed.conf /etc/init/cups-browsed.conf.stop
```

---

### Post by Rgc183 on 2014-05-01
But when I disable the browsing off, it wont search for any of the printer and it wont detect the other printers as well. I have 5-6 printers on the network of which I need only specific printers which I can select. I dont want others in my list.

---

### Post by Morbius1 on 2014-05-01
You are correct. It's an all or nothing affair.

But cups-browsed was designed to do the searching and configuration of these remote printers automatically by itself. 

If you disable the service you can still search for printers using dnssd, ipp, smb, etc .. but you will have to do it through the "Printers" utility.

---

### Post by Morbius1 on 2014-05-01
I'm shutting down for the day so if you are still having an issue with this I have a suggestion.

Start the service up again:
```
sudo service cups-browsed start
```
[COLOR=#0000cd] *This is assuming you haven't renamed it yet.*[/COLOR]

Then confirm that all these printers ar back in the Printers utility.

Now run the following command:
```
sudo cat /etc/cups/printers.conf | grep DeviceURI
```

You should get a list of how cups-browsed originally found your printers and with what protocol.

Now you can stop the service and have a guide to how to set up only the one's you want using the printer utility.

---

