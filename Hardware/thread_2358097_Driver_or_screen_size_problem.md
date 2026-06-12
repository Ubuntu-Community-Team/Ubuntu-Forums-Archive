---
title: "Driver or screen size problem??"
date: 2017-04-09
forum: Hardware
---

### Post by lancefarrah on 2017-04-09
Hello all,

First I apologize that I have very little to offer as far as linux is concerned but I have a linux problem. I am converting this Kiosk from windows 7 to lubuntu. I am using an usb drive to boot up the machine. 
[IMG]http://pasteboard.co/2jH5vKKyu.jpg[/IMG]

if you cant see the image it says:
 
try lubuntu without install
install lubuntu
etc
etc

but once I click anything it fades to black. I am guessing it might have found a screen size it's not familiar with it. But using the randr command seems you have to know what the name of the device and if lubuntu wont display how to I write the command? 

I am not sure if I explained the problem well. But if someone in Michigan understands the issue I have no problem paying for hands on help. 

Thanks

---

### Post by gordintoronto on 2017-04-10
Almost all the time, this is solved by using nomodeset, which is a boot option. See this web page:
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

