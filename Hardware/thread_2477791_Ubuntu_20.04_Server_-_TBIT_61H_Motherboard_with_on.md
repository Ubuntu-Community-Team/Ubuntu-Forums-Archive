---
title: "Ubuntu 20.04 Server - TBIT 61H Motherboard with onboard 10/100 Ethernet Adapter"
date: 2022-08-07
forum: Hardware
---

### Post by zane786 on 2022-08-07
Hi 

Just cant seem to get my Ubuntu 20.02 Server installation to see my Network adapter.
I have a TBIT H61 Motherboard(in a Tower PC) and I'm using the onboard 10/100 Network Port(RJ45 Port just above the 3 coloured Audio Ports)
I suspect the vendor is Realtek, but not 100% sure.

Please advise how I can check which driver vendor+model I require and where I could download the driver/drivers

---

### Post by oldfred on 2022-08-08
What does this show?
[FONT=monospace][COLOR=#000000]sudo lshw -sanitize | grep -m 1 -A 25 "*-network"[/COLOR]

# Plug in Ethernet cable and see if errors:
dmesg | tail -n10

I only knew my new motherboard initially had power when Ethernet port lights came on.

[/FONT]

---

### Post by zane786 on 2022-08-09
Output of commands in screenshots
Its only my USB connected mobile phone connection Im using to get temp internet access for mu ubuntu updates 
I tried to compile the r8* drivers(r8125) - see screenshot - I suspect Realtek is the manufacturer of my network adapter , but it comes up with SSL/cert errors

---

### Post by oldfred on 2022-08-09
Please do not post screen shots of terminal output.
Copy & paste the text and use code tags if longer.  # in Advanced editor.
If Ethernet or WiFi not working copy to a text file & use it to copy to forum.

Do you have UEFI Secure Boot on?
That requires you to create your own Security Key to add any proprietary drivers.

---

