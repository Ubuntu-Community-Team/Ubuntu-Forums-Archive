---
title: "Installing ISDN modem FRITZ! Card USB"
date: 2009-01-14
forum: Hardware
---

### Post by shortmanikos on 2009-01-14
First of all I would like to clarify that I am not using Ubuntu but Debian Lenny. The problem I am facing is not distro - specific so I took the liberty of asking help from here as well.

I am having trouble installing modem FRITZ! Card USB v2.1 ([_[COLOR="Navy"]here at company's site[/COLOR]_](http://www.avm.de/en/Produkte/FRITZ_for_ISDN/FRITZ_Card_USB/index.html)) in Debian Lenny (kernel 2.6.26-1). This modem is my only access to the internet (I am now unfortunately writing from Vista) so it is a crucial matter to me... The company [_[COLOR="Navy"]provides drivers and firmware[/COLOR]_](http://www.avm.de/en/frame/frame.php?destination=http%3A%2%2Fwebgw.avm.de%2Fdownload%2FDownload_en.jsp%3Flang%3Den%26preferlang%3Den%26os%3Dlinux%26product%3DFRITZ!Card+USB+v2.x%26category%3Dfritzisdndsl) only the drivers will not compile (on newer kernels) (I am not a totally new user - kernel sources etc are installed- I 've compiled modules for other devices). So far the best I could do was by using this [_[COLOR="Navy"]guide[/COLOR]_](http://www.panticz.de/?q=compile_ubuntu_avm_fritz_card_usb) I get the error mentioned [[COLOR="Navy"]_here_[/COLOR]](http://www.panticz.de/?q=node/165). I am not running the script (it wouldn't work since I don't have internet) I patch the files and then run make. The error message I get is identical. 

A working source or the .ko file (fcusb2.ko I think) compiled for kernel 2.6.26-1 or any other suggestion would be a real saver.

Thanks in advance.

---

