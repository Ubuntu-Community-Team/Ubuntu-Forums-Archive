---
title: "How to pass printing password via CUPS"
date: 2011-02-24
forum: Hardware
---

### Post by david@iprop on 2011-02-24
Hi there,

I had a Xerox DocuCenter-II C3000 driver setup in u10.10 with the printer on the LAN. Everytime I send a print job it got busted with error code 016-757 which translate to invalid username and password (known issue).

My question is where is the location that i could input the authentication via CUPS configuration? The printer password is standalone username and password authentication.

Thanks

---

### Post by Morbius1 on 2011-02-24
Don't know anything about your particular printer but I guess it depends on how it's server is set up. Perhaps it's set up as a SMB or Samba server. Or perhaps it's set up as a CUPS server.

Go into **/etc/cups/printers.conf** on your Ubuntu machine and for that printer look for the line that starts with "DEVICE_URI=".

If it starts with: DEVICE_URI="smb://, then the general syntax with authentication would be:
```
smb://username:password@server/printer
```If it starts with: DEVICE_URI="ipp://, then it's a similar syntax, for example:
```
ipp://username:password@server:631/printers/printername
```

---

### Post by david@iprop on 2011-02-24
the URI is below

```
dnssd://DocuCentre-II%20C3000%20%20(38%3Affffffca%3Afffffff0)._printer._tcp.local/
```

---

### Post by Morbius1 on 2011-02-25
I honestly don't know. I've never used avahi ( dnssd ) to access a printer like that. You can try to apply the same syntax as the other protocols since it seems they all follow the same pattern but that's just a guess:
```
dnssd://username:password@DocuCentre-II%20C3000%20%20(38%3Affffffca%3Afffffff0)._printer._tcp.local/
```Then restart cups:
```
sudo service cups restart
```

---

### Post by david@iprop on 2011-02-27
It doesn't work

---

### Post by david@iprop on 2011-02-28
What i learnt was for dnssd to work, a txt file will be send to the service rather than passing thru username and password within the url and the username and password will be treated as user ID on the print job.

any help is appreciated!

---

