---
title: "Missing Driver"
date: 2009-06-26
forum: Hardware
---

### Post by pablogutierrez05 on 2009-06-26
Hello,

I am new to Ubuntu, or any Linux distribution for that matter, and to be honest, I don't know much about Linux at all but am really trying to learn. As I was playing around with the settings, I activated my wifi driver and the next time I turned my computer I cannot connect to the internet because it is gone from the hardware section under Administration. Please help, I am open to any solution, even if it means reinstalling Ubunu! 

Thank You!

---

### Post by Steelmourne on 2009-06-26
Maybe it wasn;t necessary to activate the driver if it was working. Can you type \

lspci -vv -nn > hardware.txt

in terminal. Then type exit. Open up your home folder and the .txt file and search with Ctrl+F for wireless. Post the make and model.

Then type sudo lshw -C network in terminal and see what it says for your wireless card wheter enabled, disabled or unclaimed.

---

### Post by pablogutierrez05 on 2009-06-27
First of all, I would like to thank you,
 
 I did what you told me, but when I searched for wireless in the .txt file it said "phrase not found."
 
 However, when I typed sudo lshw -C into the terminal it said the product was
 
 RTL8101E/RTL8102E PCI Express Fast Ethernet Controller 

and it said my wireless card is disabled, saying 
 
 *-network DISABLED
        description: Ethernet interface
 
 Thanks Again!

---

### Post by Ayuthia on 2009-06-27
Can you check that .txt file and see if there is an Ethernet Controller or Network Controller?  The one that you listed is your wired card.  Thanks!

---

### Post by pablogutierrez05 on 2009-06-27
Hi,

In the .txt file this is what it says next to Ethernet controller:

Ethernet controller [0200] : Realtek Semiconductor Co. , Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet Controller [10ec : 8136] (rev 02)

---

### Post by Ayuthia on 2009-06-27
Can you attach the hardware.txt file in your next post?  The card that you are listing is your wired ethernet card.  However, it does seem that lshw -C network knows that your wireless card is there.  In your lshw -C network results, does it list another card name besides the Realtek one?

Also, have you tried going into NetworkManager and verify that it is set for Roaming? 

The lshw -C network information says that it is disabled but not unclaimed.  That sounds like the driver is there, but something has your card turned off.

---

### Post by pablogutierrez05 on 2009-06-27
Hi, 

My hardware.txt is attached, as well as the lshw -C.

Thanks So Much!

---

### Post by Ayuthia on 2009-06-27
Can you redo the lshw -C network command again?  It looks like you might typed something incorrectly because your attachment is showing the help information.

As for your lspci information, it does not show your wireless card.  That could mean that your wireless card is for some reason located in lsusb as a USB device or it could mean that there is a hardware problem.  If you have Windows installed on this computer, you might want to check and see if it works in there.

Also, what model of HP are you using?  I am assuming it is an HP based on your lspci information.

---

### Post by pablogutierrez05 on 2009-06-27
Hi,

Sorry, here is the lshw -C network.

Also, I tried and I could connect to the internet in Windows.

My laptop is an HP Compaq Presario CQ60.

Thank You!

---

### Post by Ayuthia on 2009-06-27
> **pablogutierrez05 said:**
> Hi,

Sorry, here is the lshw -C network.

Also, I tried and I could connect to the internet in Windows.

My laptop is an HP Compaq Presario CQ60.

Thank You!

The info was not attached.  Can you send it again?

---

### Post by pablogutierrez05 on 2009-06-27
Hi,

Sorry, here it is

   WARNING: you should run this program as super-user.
    *-network               
         description: Ethernet interface
         product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
         vendor: Realtek Semiconductor Co., Ltd.
         physical id: 0
         bus info: pci@0000:01:00.0
         logical name: eth0
         version: 02
         serial: 00:1f:16:6e:58:3d
         width: 64 bits
         clock: 33MHz
         capabilities: bus_master cap_list ethernet physical
         configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 module=r8169 multicast=yes
    *-network DISABLED
         description: Ethernet interface
         physical id: 2
         logical name: pan0
         serial: 7a:f2:15:79:b4:4d
         capabilities: ethernet physical
         configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

---

### Post by Ayuthia on 2009-06-27
I am thinking that this might be a hardware issue.  Usually lspci or lshw -C network will show your wireless card information.  Neither one of these commands are doing it.  

Can you provide the lsusb information?  If it does not show up there, then I am definitely leaning towards a hardware issue unless you are able to get the wireless card to work using another operating system.

---

