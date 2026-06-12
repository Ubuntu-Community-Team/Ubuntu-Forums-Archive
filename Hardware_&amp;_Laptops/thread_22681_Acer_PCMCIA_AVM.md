---
title: "Acer PCMCIA AVM"
date: 2005-03-29
forum: Hardware &amp; Laptops
---

### Post by anarchill on 2005-03-29
Hi!

I ve installed Hoary on my Acer Travelmate 290. I wanted to use my AVM Fritz Card PCMCIA to connect to the internet, but it does actually not work. I ve also read the HowTo but all I get ist

after pon isdn/myprovider

PLugin userpass.so loaded. 
userpass: $Revision: 1.5 $ 
Plugin capiplugin.so loaded 
capiplugin: $Revision: 1.36 $ 
capiconn: 1.10 
capiplugin: CAPI_REGISTER failed - CAPI not installed (0x1009) [No such device or address (6)] 


any idea??

---

### Post by ZaphodX on 2005-10-03
Hi!

You posted this issue some time ago. But perhaps this may be helpful for others, too.

I've just bought a Laptop and decided to use Ubuntu. Good decision, I really like it! 

Today I've got my hands on an AVM Fritz!Card PCMCIA. 
I've downloaded the most recent driver from AVM's homepage:
[ftp://ftp.avm.de/cardware/fritzcrd.pcm/linux/suse.93/fcpcmcia-suse93-3.11-07.tar.gz]("ftp://ftp.avm.de/cardware/fritzcrd.pcm/linux/suse.93/fcpcmcia-suse93-3.11-07.tar.gz")

It does contain binary modules for SuSE9.3's kernel only. But fortunately it also comes along with the full Open Source code.
So I installed Ubuntu's capiutils and the linux-source. The linux-header headers should do instead of the whole source...

After that, compilation of the AVM driver was a simple 'tar xvfz' and an './install'.

But then, after pluggin in the card,  the kernel said: "pcmcia: fcpcmcia_cs lacks a requisite callback function"
Ooops. Something's wrong with the driver!

So I dug into the source code and found the bug.
There's a line missing in fritz/src/fcpcmcia_cs.c:

```
static struct pcmcia_driver cs_driver = {
        .owner  = THIS_MODULE,
        .drv    = {
                .name   = "fcpcmcia_cs",
        },
        .attach = cs_attach,
        .detach = cs_detach,
        .event  = cs_event,
};
```

The missing line is ".event  = cs_event,"

After adding this patch, another ./install will compile a working driver.

Now, inserting the card and an 
/etc/init.d/capiutils restart 
will start the capi support for the card.

pppd call isdn/avm 
worked at once. (/etc/ppp/peers/isdn/avm is a test configuration. The card will call avm's test server in Germany! :)

My only concern now is, how to safely remove the card and re-insert it without booting. I'm a complete noob in using notebooks :)

Carsten

---

