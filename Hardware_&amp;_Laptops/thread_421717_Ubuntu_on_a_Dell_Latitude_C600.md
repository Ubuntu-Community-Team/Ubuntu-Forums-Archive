---
title: "Ubuntu on a Dell Latitude C600"
date: 2007-04-24
forum: Hardware &amp; Laptops
---

### Post by andrew_howlett on 2007-04-24
Hi all,

Installed Edgy and Feisty on a Dell Latitude C600.

[Posted the experience here for future reference.]("http://radagast.bglug.ca/laptop/ubuntu_on_latitude_c600.html")

Maybe it will help others.

later,
Andrew.

---

### Post by Mumra on 2007-05-12
Hi - I have pulled up Feisty on a C600 also, and done another little article. This should help anyone with the mouse freezing issue or who has one of the high res displays (the 1440 by 1080 one).

[http://www.shahidhussain.com/blog/?p=12](http://www.shahidhussain.com/blog/?p=12)

---

### Post by n3tfury on 2007-10-19
> **Mumra said:**
> Hi - I have pulled up Feisty on a C600 also, and done another little article. This should help anyone with the mouse freezing issue or who has one of the high res displays (the 1440 by 1080 one).

[http://www.shahidhussain.com/blog/?p=12](http://www.shahidhussain.com/blog/?p=12)

you my friend are my hero.  i just got done installing/reinstalling 4 different distros because of the mouse freezing issue.  thank you SO much.

---

### Post by whitelotus9 on 2007-10-19
I just burned Gutsy Gibbon onto a Cd for installing on my Dell Latitude C600.  I have a LinkSys WiFi card that I purchased new via eBay for this laptop.  It hasn't arrived yet though.  With Windows adding new hardware is relatively easy after the OS has been installed on a new system. This is my first time going with Ubuntu.  My question is do I need to wait for the WiFi card to arrive before doing the Ubuntu install onto the laptop or will it properly sense the card once inserted if I install Ubuntu before the card arrives?  Thank you in advance. Michael

---

### Post by n3tfury on 2007-10-19
i don't know that answer Michael, but someone will chime in.  you might want to include the model # of your card though.

---

### Post by whitelotus9 on 2007-10-20
The model number of my Linksys card is WPC11 and it's Ver 4.  This is a PCMCIA card for the laptop.

---

### Post by Gunner_Sr on 2007-10-20
Did you guys having any fan/heating problems? Did you use i8k?

Thanks.

---

### Post by n3tfury on 2007-10-20
> **whitelotus9 said:**
> The model number of my Linksys card is WPC11 and it's Ver 4.  This is a PCMCIA card for the laptop.

[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys)

looks like you're good to go.  what i would do though is plug it in before you boot up.  i'm not sure if it will automatically recognize while the system is up.

---

### Post by sbennettgso on 2007-10-20
I've got a WPC11 v4 that I used under Feisty.  When I installed Xubuntu Gutsy, the card seems to be recognized but when it associates with a wiereless network, it hangs and the scroll lock and caps lock indicators on my computer (ThinkPad A22p) begin to flash.  So I don't know what's up with that.

Thanks,
Scott

---

### Post by whitelotus9 on 2007-10-20
In the case of my home network, before the Linksys will see the internet I'll need to enable WEP and load the security code.  With Gutsy, how would that be done?  Again please excuse my newbie questions.  Thank you!

---

### Post by n3tfury on 2007-10-20
> **whitelotus9 said:**
> In the case of my home network, before the Linksys will see the internet I'll need to enable WEP and load the security code.  With Gutsy, how would that be done?  Again please excuse my newbie questions.  Thank you!

click on the network icon in the task bar and it should "see" and list your network.  click the radio button next to it and it will prompt you for your key.  you can enter manual settings there also.

---

### Post by hyperq on 2007-10-21
> **sbennettgso said:**
> I've got a WPC11 v4 that I used under Feisty.  When I installed Xubuntu Gutsy, the card seems to be recognized but when it associates with a wiereless network, it hangs and the scroll lock and caps lock indicators on my computer (ThinkPad A22p) begin to flash.  So I don't know what's up with that.

Thanks,
Scott

I have the same issue.  I am using a LinkSys WPC11 v4 cardbus laptop card on Thinkpad T21.  It works in 7.10 without using any encryption.  When I enable WEP encryption, the laptop hangs and both the scroll lock and caps lock indicators start blinking.  Then I saw in the /var/log/syslog that it is using linux driver rtl8180 which doesn't have WEP encryption support.  

The card works fine in Ubuntu 7.04 with WEP encryption and the build-in linux driver, but I am not sure whether Ubuntu 7.04 is using rtl8180 or not.

---

### Post by whitelotus9 on 2007-10-21
My original question is still unanswered....   Does Gutsy (or Ubuntu for that matter) support "plug and play"?  
 
WIll it recognize newly installed hardware and load or prompt to load the necessary drivers, etc.?

---

