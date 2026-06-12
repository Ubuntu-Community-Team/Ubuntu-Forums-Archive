---
title: "Brother Printer Install"
date: 2016-07-20
forum: Hardware
---

### Post by angel mike on 2016-07-20
I have a Brother Printer HL-3150CDW and using Ubuntub14.04 I am having difficulty connecting it to my PC computer - it is a network printer which I can use from another laptop using a wireless connection. The PC computer is hard wired to the router and I have installed the driver using CUPS and the Brother download site. 
It shows up on the screen as a network printer but when I send a job to the print queue I says not connected.  Thanks Mike

---

### Post by SeijiSensei on 2016-07-20
Did you use the "[driver install tool]("http://support.brother.com/g/b/downloadlist.aspx?c=eu_ot&lang=en&prod=hl3150cdw_eu&os=128")" at the Brother site?  If not, give that a try.  It works fine to connect my machines to my HL-3170CDW.

Another option is to visit [http://localhost:631/](http://localhost:631/) on the PC and use the Add Printer function.  Usually the Brother will appear in the list of "discovered" printers.

I'm assuming that the PC and the printer are in the same network subnet, presumably the same one as the machine using wifi is on.

---

### Post by him610 on 2016-07-20
> Did you use the "driver install tool" at the Brother site?
I give a strong second to the "driver install tool." It has worked on five different computers on my network, including those connected wirelessly. My machine is a Brother MFC-7360. I did assign a static IP address to mine, though.

---

### Post by angel mike on 2016-07-21
Thanks for the responses - yes I used the brother install tool and it seemed to install the drivers/wrappers - have used it before with success. All the devices are on the same network. The Gateway PC GM5066b is hardwired to the router whilst the more up to date laptop is wireless and connects to the printer okay usuing the same driver install method. . I suspect it may be the ip address that is the problem. I will have a go with the 631 site as suggested, Many thanks. Mike

---

### Post by kurt18947 on 2016-07-21
There's another printer administration tool I find useful - "system-config-printer". It's the default printer administration tool in some of the 'flavors" such as Xubuntu, Lubuntu & Ubuntu-Gnome. It's available in the repositories.

---

### Post by angel mike on 2016-07-22
Thanks Kurt will give it a try - much appreciated ! I thought I had mastered the Brother printer install - still I learn more about the Ubuntu system ! Mike

---

### Post by angel mike on 2016-07-22
I,ve solved it ! Kurt gave me a glue about resetting the IP. So I used my laptop to view the printer settings which were Device URI lpd://BRN30055C3D7253/BINARY_P1 and put these in on my PC - low and behold I am connected and the little blue circle with an i on the logo is gone - just a green tick remaining. So the Brother printer installer route came up 'Trumps' 
Thanks for all your responses. Mike

---

### Post by kurt18947 on 2016-07-22
Hi Mike

I'm glad you have a handle on it. I generally use an old and tattered method that has proven very reliable for networked machines for me. I assign a static address to the printer. For machines with fax keypads that's generally pretty straightforward. To make it easy to remember i.p. addresses I use the machine's model number, For example, an MFC-J470's I.P. address might be 192.168.1.47.  Opening the 'system-config-printer' app I find the screen with 'device URI' and using the previous example I would enter this:

```
socket://192.168.1.49:9100
```

I'd had problems with earlier Ubuntu 'forgetting' where to find the printer.  Using this procedure I've never 'lost' a printer. The newer methods might be more reliable but if you have issues with the printer being 'lost', this technique has been successful for me.

---

### Post by angel mike on 2016-07-23
Hi Kurt
Thanks for that useful reference - filed for next time ! 
As a matter of interest the 'socket' ref has not changed on my printer properties being the IP address sockett://192.168.1.64. The 'lpr' address I used for the 'Device URI' to finally connect is listed on the output of the printer settings under <netBIOS Name> BRN30055C3D7253. I have no idea what this means but it worked !
Thanks once again for all your help - a great forum !
 Mike

---

