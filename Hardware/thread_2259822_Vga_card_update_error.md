---
title: "Vga card update error"
date: 2015-01-07
forum: Hardware
---

### Post by gshyuk on 2015-01-07
My laptop specifications are as follows:
Toshiba Satellite C50-A pscjek-03e00w
Intel Beytrail Pentiam N3520
DDR3L Memory 4GB
Intel HD Graphics
MS Windows 8.1


By buying this laptop has a window away and started to use Linux. 
But this feeling of unity Ubuntu and Mint Mate 
MS Windows 8 all-prone than slow the system down.


I tried to install the latest Debian.
Show only tty modes after installation and X-window approach was not possible.
I tried to boot from the Mint Debian Live USB.
You must login screen sound heard was only darkness.
But do you use Virtualbox screen came out normal.


I am using Linux now LXLE. Lift is really nice and light and love it.
screenshot:[http://thumbnail.egloos.net/600x0/http://pds27.egloos.com/pds/201501/06/16/f0150916_54aae8a5219b5.jpg](http://thumbnail.egloos.net/600x0/http://pds27.egloos.com/pds/201501/06/16/f0150916_54aae8a5219b5.jpg)
[IMG]http://thumbnail.egloos.net/600x0/http://pds27.egloos.com/pds/201501/06/16/f0150916_54aae8a5219b5.jpg[/IMG]

But figured leads to downtime symptoms. John while light Internet surfing.


[[https://01.org/linuxgraphics/downloads]](https://01.org/linuxgraphics/downloads]) from the [Graphics Installer 1.0.7 for Ubuntu * 14.04, 64-bit] Download the've run.
However, the upgrade was an error.
screenshot: [http://ubuntu-kr.org/download/file.php?id=14600](http://ubuntu-kr.org/download/file.php?id=14600)
[[IMG]http://ubuntu-kr.org/download/file.php?id=14600[/IMG]]("http://ubuntu-kr.org/download/file.php?id=14600")


In fact, you can not always slow down or even WiFi or lost.


But the problem is too big, Ubuntu and Mint is eat less resources, Windows 8, a heavier feel naguyo. This is sometimes boring downtime will occur.


Why is that? Is there a workaround?

[Transfer 1]






Specification of my laptop, is as follows.
Toshiba Satellite C50-A pscjek-03e00w
Intel Beytrail Pentiam N3520
DDR3L Memory 4GB
Intel HD Graphics
MS Windows8.1


While buying this laptop, off the window, I started using Linux. However, Ubuntu of unity and mint, slower than all use impression Mate MS Windows8, system down was Jatoato.


Recently I tried to install the Debian.
Appears after installation tty mode only, was Mashi impossible is X-window of access.
I tried to to boot up with a mint Debian live USB.
Only login voice heard screen, was just dark.
However, if you use the Virtualbox, screen came out successfully.


I Linux to now use is LXLE. It takes really fashionable like to lightly.
screenshot: http: //thumbnail.egloos.net/600x0/http: //pds27.egloos.com/pds/201501/06/16/f0150916_54aae8a5219b5.jpg


However, you still occur symptoms of system down. I even during web surfing of light Internet.


I download and run the [Graphics Installer1.0.7 for Ubuntu * 14.04,64-bit] in [[https://01.org/linuxgraphics/downloads]](https://01.org/linuxgraphics/downloads]).
However, I get the upgrade error.
screenshot: http:? //ubuntu-kr.org/download/file.php id = 14600


In fact you might be Wi-Fi also may become occasionally slow, or cut.


However, still a big problem, Ubuntu Noto mint eat less resources than Windows 8, heavier feel Naguyo. Is that system down sometimes occur.


Why not? What solutions?



[Transfer2]



Thank you.

---

### Post by schragge on 2015-01-07
The certificate of download.01.org is signed with CA certificate
[http://crt.comodoca.com/COMODORSADomainValidationSecureServerCA.crt](http://crt.comodoca.com/COMODORSADomainValidationSecureServerCA.crt)
which is probably not in your /etc/ssl/certs/ca-certificates.crt

To find it out, I did
```

echo -n | openssl s_client -showcerts -connect download.01.org:443 2>/dev/null |
sed '/-BEGIN/,/-END/!d' | openssl x509 -noout -text | sed -n '/CA Issuers/s/.*URI://p'

```

See [this]("http://askubuntu.com/a/377570") for how to install it on your system.

---

