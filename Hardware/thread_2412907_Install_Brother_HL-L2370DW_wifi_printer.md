---
title: "Install Brother HL-L2370DW wifi printer"
date: 2019-02-18
forum: Hardware
---

### Post by makitso on 2019-02-18
Having a bit of trouble configuring this wifi printer.  Have the drivers downloaded and have run the script.  But, don't know what URI I should be using and what Brother drivers, CUPS, etc?

---

### Post by brian_p on 2019-02-19
Do yourself a favour and put the device on the network. Then

[list]Uncomment *CreateIPPPrinterQueues All* in /etc/cups/cups-browsed.conf.[/list]
```
systemctl restart cups-browsed 
```

---

### Post by makitso on 2019-02-21
@[COLOR=#DD4814][COLOR=#000000][brian_p]("https://ubuntuforums.org/member.php?u=543421")  Thanks for the keen insight![/COLOR][/COLOR]

---

