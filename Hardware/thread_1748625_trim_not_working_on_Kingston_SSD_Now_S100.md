---
title: "trim not working on Kingston SSD Now S100"
date: 2011-05-03
forum: Hardware
---

### Post by gettons on 2011-05-03
I can't get the trim working on this ssd although it is supported on ext4 fs from kernel 2.6.33 onwards.
I have tried with ubuntu maverick 32 bit and the discard option, AHCI enabled in the bios too but with no success. ( device is a Zotac ZBOXHD-ND22-B ) 
To test whether or not the trim is working I am using the dd test you can find in here [http://www.google.com/url?sa=t&source=web&cd=2&ved=0CCkQFjAB&url=http%3A%2F%2Fsites.google.com%2Fsite%2Flightrush%2Frandom-1%2Fcheckiftrimonext4isenabledandworking&rct=j&q=check%20trim%20ubuntu&ei=ypbATbCAMYS08QPMkfTNBQ&usg=AFQjCNFg_YUAFCXMejx_lNDM3z6V-A6Cxg&sig2=kSqnOPsj2fHX2kboNBHO1w&cad=rja]("http://www.google.com/url?sa=t&source=web&cd=2&ved=0CCkQFjAB&url=http%3A%2F%2Fsites.google.com%2Fsite%2Flightrush%2Frandom-1%2Fcheckiftrimonext4isenabledandworking&rct=j&q=check%20trim%20ubuntu&ei=ypbATbCAMYS08QPMkfTNBQ&usg=AFQjCNFg_YUAFCXMejx_lNDM3z6V-A6Cxg&sig2=kSqnOPsj2fHX2kboNBHO1w&cad=rja")
I have tried to:
Using different kernels/os versions ( ubuntu natty narwhal )
enable/disable AHCI DID linux in the bios
enable/disable AHCI in the bios
enable/disable SATA mode in the bios

But I keep getting the same sequence of letters/numbers, instead of zeroes.

---

### Post by cremersdh on 2011-09-23
> **gettons said:**
> I can't get the trim working on this ssd although it is supported on ext4 fs from kernel 2.6.33 onwards.
I have tried with ubuntu maverick 32 bit and the discard option, AHCI enabled in the bios too but with no success. ( device is a Zotac ZBOXHD-ND22-B ) 
To test whether or not the trim is working I am using the dd test you can find in here [http://www.google.com/url?sa=t&source=web&cd=2&ved=0CCkQFjAB&url=http%3A%2F%2Fsites.google.com%2Fsite%2Flightrush%2Frandom-1%2Fcheckiftrimonext4isenabledandworking&rct=j&q=check%20trim%20ubuntu&ei=ypbATbCAMYS08QPMkfTNBQ&usg=AFQjCNFg_YUAFCXMejx_lNDM3z6V-A6Cxg&sig2=kSqnOPsj2fHX2kboNBHO1w&cad=rja]("http://www.google.com/url?sa=t&source=web&cd=2&ved=0CCkQFjAB&url=http%3A%2F%2Fsites.google.com%2Fsite%2Flightrush%2Frandom-1%2Fcheckiftrimonext4isenabledandworking&rct=j&q=check%20trim%20ubuntu&ei=ypbATbCAMYS08QPMkfTNBQ&usg=AFQjCNFg_YUAFCXMejx_lNDM3z6V-A6Cxg&sig2=kSqnOPsj2fHX2kboNBHO1w&cad=rja")
I have tried to:
Using different kernels/os versions ( ubuntu natty narwhal )
enable/disable AHCI DID linux in the bios
enable/disable AHCI in the bios
enable/disable SATA mode in the bios

But I keep getting the same sequence of letters/numbers, instead of zeroes.

Did you ever solve this ? I am having the same problem with the S100 and am curious if you found a solution

---

