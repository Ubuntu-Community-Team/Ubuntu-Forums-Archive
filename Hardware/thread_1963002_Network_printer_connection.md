---
title: "Network printer connection"
date: 2012-04-21
forum: Hardware
---

### Post by bilkay on 2012-04-21
I'm trying to connect to a network Brother MFC-9325CW printer. I downloaded and installed the LPR and cupswrapper drivers (deb) from the brother.com website. Everything looks OK until I try to print something. Then I get an error and after running the diagnostic, I get an explanation:

[INDENT]**Queue Not Enabled**

The queue 'Brother-MFC-932SCW' s not enabled. The reason
given is: 'Unable to locate printer 'BRWE4DS3D3LCC3D' !'

To enable it, select the 'Enabled' checkbox in the 'Policies'
tab for the printer n the printer administration tool. To start
this tool, select System->Administration->Printing from the
main menu.
[/INDENT]
The "Enabled" checkbox **was** checked, but is now unchecked. After checking the checkbox again, a subsequent print job yields the same error and diagnostic.

Am I missing something?

---

### Post by ahallubuntu on 2012-04-21
Are you able to print to this printer via USB?  Make that work first if not.

---

### Post by bilkay on 2012-04-21
> **ahallubuntu said:**
> Are you able to print to this printer via USB?  Make that work first if not.
That's not an option (it's not my printer).

I forgot to mention that:
a) The ubuntu version is 10.04 LTS,
b) I can print to this network printer from this laptop when running Windows 7.

---

### Post by ahallubuntu on 2012-04-21
Did you try installing the printer using its IP address on the network?

On a Brother, if you don't know the IP address, typically you can hold down the Status button (or "Go" or whatever the main button is) for about 10 seconds and it will spit out a printed page of network stuff including the IP address.  Try using that to install it over the network.

---

### Post by kurt18947 on 2012-04-22
Not being your printer may be an issue with what I'm about to suggest.  I had problems with a networked printer working fine immediately after installation but upon restarting it wasn't found, sort of like the O.P. is finding.  I assigned a static I.P. address to the printer.  Then go to printing -> properties -> Device URI.  I just put the following:

```
socket://192.168.xxx.xxx:9100
```I'm not sure this would work if the printer does not have a static I.P. address.  That  proved very reliable in Ubuntu 10.04 & 10.10.

---

### Post by bilkay on 2012-04-22
> **kurt18947 said:**
> Not being your printer may be an issue with what I'm about to suggest.  I had problems with a networked printer working fine immediately after installation but upon restarting it wasn't found, sort of like the O.P. is finding.  I assigned a static I.P. address to the printer.  Then go to printing -> properties -> Device URI.  I just put the following:

```
socket://192.168.xxx.xxx:9100
```I'm not sure this would work if the printer does not have a static I.P. address.  That  proved very reliable in Ubuntu 10.04 & 10.10.
That's the solution. Thanks a lot.

---

### Post by kurt18947 on 2012-04-24
> **bilkay said:**
> That's the solution. Thanks a lot.

I'm glad it worked out for you.  Could you mark the thread solved?  That might help others searching for a solution to a similar problem.  Thread tools near the top of the page should do it.

---

### Post by bilkay on 2012-04-29
One thing I learned is that it's a heck of a lot easier to add printers using [http://localhost:631/printers](http://localhost:631/printers) than the gnome printer admin. tool.

---

