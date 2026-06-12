---
title: "Laptop for Ubuntu and Windows 8"
date: 2013-04-22
forum: Hardware
---

### Post by abovett on 2013-04-22
Hi all

I'm looking for recommendations for a laptop for dual-booting Windows 8 and Ubuntu - I'm a Linux user by choice but need to support Windows 8 users so I need something to run it on and none of my current machines are available or suitable. I'm thinking probably in the £300 to £500 price range (though could stretch a bit further if I have to). Performance is not too critical but I would like reasonable portability, so no more than 14 or 15 inch screen tops, but with a decent resolution. Good Ubuntu compatibility is a must. Ideally, I'd also like confirmation that it's possible to get into the UEFI settings and (if necessary) load your own keys. I've started scouring the compatibility list but there's so much in there that it's hard to know where to start so suggestions are welcome.

Thanks

Andy

---

### Post by roly33 on 2013-04-22
> **abovett said:**
> Hi all

I'm looking for recommendations for a laptop for dual-booting Windows 8 and Ubuntu - I'm a Linux user by choice but need to support Windows 8 users so I need something to run it on and none of my current machines are available or suitable. I'm thinking probably in the £300 to £500 price range (though could stretch a bit further if I have to). Performance is not too critical but I would like reasonable portability, so no more than 14 or 15 inch screen tops, but with a decent resolution. Good Ubuntu compatibility is a must. Ideally, I'd also like confirmation that it's possible to get into the UEFI settings and (if necessary) load your own keys. I've started scouring the compatibility list but there's so much in there that it's hard to know where to start so suggestions are welcome.

Thanks

Andy


How about [this]("http://www.novatech.co.uk/laptop/range/novatechnspiren1536.html") you can get it with Windows 7, Windows 8 and No OS.  I'd personally go for the no OS version as if their is UEFI it'll more than likely be off by default then Install Windows 8 and Ubuntu.

Roland

---

### Post by oldfred on 2013-04-22
I have not seen anyone attempt to load their own keys. Currently Ubuntu is using the older version of shim. And shim currently uses the Microsoft key.

 UEFI generic shim - Secure Boot bootloader
[http://mjg59.dreamwidth.org/20303.html](http://mjg59.dreamwidth.org/20303.html)
      
 Matthew Garrett's Blog
[URL="http://mjg59.dreamwidth.org/"]http://mjg59.dreamwidth.org/
[/URL]
 James Bottomley's random Pages - Linux Foundation Secure Boot System Released
[http://blog.hansenpartnership.com/linux-foundation-secure-boot-system-released/](http://blog.hansenpartnership.com/linux-foundation-secure-boot-system-released/)

But we are seeing many systems that have been modified to only boot the Windows efi file. We have to back it up, rename shim to be the Windows file and use grub to boot the backed up Windows efi file. I would think even if you could install a new key on those systems it would not work.


 Vendors violated UEFI specs - [http://hwe.ubuntu.com/docs/ubuntu-bios-uefi-requirements.pdf](http://hwe.ubuntu.com/docs/ubuntu-bios-uefi-requirements.pdf)
Firmware should not enforce any boot policy other than the mechanism specified in Section 3 of the
UEFI 2.3.1 specification [UEFI 2.3.1]. Specifically, firmware should not modify boot behaviour de-
pending on the Description field of the EFI_LOAD_OPTION descriptor.





[URL="http://mjg59.dreamwidth.org/"]
[/URL]

---

### Post by abovett on 2013-04-23
Thanks, Roland - your suggestion is useful. I was not familiar with Novatech. The machine you linked to is perhaps a little underpowered for what I want but some of the others in the range look interesting. The no OS option is certainly worth looking into.

---

### Post by abovett on 2013-04-23
Thanks for the information, Oldfred.
My thoughts on loading my own keys were based on James Bottomly's page "Bottomley: Owning Your Windows 8 UEFI Platform" 
[http://blog.hansenpartnership.com/owning-your-windows-8-uefi-platform/](http://blog.hansenpartnership.com/owning-your-windows-8-uefi-platform/)

I realise it's probably unnecessary but I prefer to "own" my platform if possible. Thanks for the warnings also - I will read up on the links you have pointed me to.
Andy

---

