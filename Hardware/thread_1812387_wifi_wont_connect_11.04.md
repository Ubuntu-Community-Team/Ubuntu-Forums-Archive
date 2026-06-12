---
title: "wifi wont connect 11.04"
date: 2011-07-26
forum: Hardware
---

### Post by Alex715 on 2011-07-26
Hi i have ubuntu 11.04 installed and am trying to get my wifi to work, i can get a list of the available networks and enable/disable my wireless but it appears that it wont let me connect to wpa and wpa2 networks.I have a thinkpad t40 with a Cisco Aironet Wireless 802.11b. I think that open and wep networks work but i cannot be sure any help would be appreciated as i need the wifi. Thanks in advance.

---

### Post by Peter09 on 2011-07-26
Can you provide the output of the terminal comand
 
```
nm-tool
```

---

### Post by Alex715 on 2011-07-26
NetworkManager Tool

State: connected

- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            e1000
  State:             connected
  Default:           yes
  HW Address:        00:09:6B:53:3C:93

  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.0.198
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1


- Device: eth1  [Auto casapepe] ------------------------------------------------
  Type:              802.11 WiFi
  Driver:            airo
  State:             connecting (configuring)
  Default:           no
  HW Address:        00:02:8A:78:9A:37

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes

  Wireless Access Points 
    casapepe:        Infra, 00:1C:F0:55:B1:C3, Freq 2422 MHz, Rate 11 Mb/s, Strength 100 WPA

---

### Post by Peter09 on 2011-07-26
Hi,
you need to do this with no wired connection - your wireless will be unavailable while you have a wired connection established.

---

### Post by Alex715 on 2011-07-26
ok sorry i didnt realise im kinda new to ubuntu


alex@Alex-Thinkpad-T40:~$ NetworkManager Tool
You must be root to run NetworkManager!
alex@Alex-Thinkpad-T40:~$ 
alex@Alex-Thinkpad-T40:~$ State: connected
State:: command not found
alex@Alex-Thinkpad-T40:~$ 
alex@Alex-Thinkpad-T40:~$ - Device: eth0  [Auto eth0] ----------------------------------------------------
-: command not found
alex@Alex-Thinkpad-T40:~$   Type:              Wired
Type:: command not found
alex@Alex-Thinkpad-T40:~$   Driver:            e1000
Driver:: command not found
alex@Alex-Thinkpad-T40:~$   State:             connected
State:: command not found
alex@Alex-Thinkpad-T40:~$   Default:           yes
Default:: command not found
alex@Alex-Thinkpad-T40:~$   HW Address:        00:09:6B:53:3C:93
HW: command not found
alex@Alex-Thinkpad-T40:~$ 
alex@Alex-Thinkpad-T40:~$   Capabilities:
Capabilities:: command not found
alex@Alex-Thinkpad-T40:~$     Carrier Detect:  yes
Carrier: command not found
alex@Alex-Thinkpad-T40:~$     Speed:           1000 Mb/s
Speed:: command not found
alex@Alex-Thinkpad-T40:~$ 
alex@Alex-Thinkpad-T40:~$   Wired Properties
Wired: command not found
alex@Alex-Thinkpad-T40:~$     Carrier:         on
Carrier:: command not found
alex@Alex-Thinkpad-T40:~$ 
alex@Alex-Thinkpad-T40:~$   IPv4 Settings:
IPv4: command not found
alex@Alex-Thinkpad-T40:~$     Address:         192.168.0.198
Address:: command not found
alex@Alex-Thinkpad-T40:~$     Prefix:          24 (255.255.255.0)
bash: syntax error near unexpected token `('
alex@Alex-Thinkpad-T40:~$     Gateway:         192.168.0.1
Gateway:: command not found
alex@Alex-Thinkpad-T40:~$ 
alex@Alex-Thinkpad-T40:~$     DNS:             192.168.0.1
DNS:: command not found
alex@Alex-Thinkpad-T40:~$ 
alex@Alex-Thinkpad-T40:~$ 
alex@Alex-Thinkpad-T40:~$ - Device: eth1  [Auto casapepe] ------------------------------------------------
-: command not found
alex@Alex-Thinkpad-T40:~$   Type:              802.11 WiFi
Type:: command not found
alex@Alex-Thinkpad-T40:~$   Driver:            airo
Driver:: command not found
alex@Alex-Thinkpad-T40:~$   State:             connecting (configuring)
bash: syntax error near unexpected token `('
alex@Alex-Thinkpad-T40:~$   Default:           no
Default:: command not found
alex@Alex-Thinkpad-T40:~$   HW Address:        00:02:8A:78:9A:37
HW: command not found
alex@Alex-Thinkpad-T40:~$ 
alex@Alex-Thinkpad-T40:~$   Capabilities:
Capabilities:: command not found
alex@Alex-Thinkpad-T40:~$ 
alex@Alex-Thinkpad-T40:~$   Wireless Properties
Wireless: command not found
alex@Alex-Thinkpad-T40:~$     WEP Encryption:  yes
WEP: command not found
alex@Alex-Thinkpad-T40:~$ 
alex@Alex-Thinkpad-T40:~$   Wireless Access Points 
Wireless: command not found
alex@Alex-Thinkpad-T40:~$     casapepe:        Infra, 00:1C:F0:55:B1:C3, Freq 2422 MHz, Rate 11 Mb/s, Strength 100 WPA
casapepe:: command not found



I know thats messed up it keeps saying comand not found down the left.

---

### Post by Peter09 on 2011-07-26
No ... just the output of the command
 
```
nm-tool
```
 
while your wired connection is disconnected.

---

### Post by Alex715 on 2011-07-26
NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000
  State:             unavailable
  Default:           no
  HW Address:        00:09:6B:53:3C:93

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: eth1 -----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            airo
  State:             disconnected
  Default:           no
  HW Address:        00:02:8A:78:9A:37

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes

  Wireless Access Points 
    casapepe:        Infra, 00:1C:F0:55:B1:C3, Freq 2422 MHz, Rate 11 Mb/s, Strength 100 WPA

the wired connection was unpluged for my last post put maybe i dint leave it long enough

---

### Post by Peter09 on 2011-07-26
try clicking on the network icon (top left) you should get a menu - can you see your acces point in there? If so click on it.

---

### Post by Alex715 on 2011-07-26
I can see my acces point and all of my neigbors but when i click on it a window comes up saying "Authentication required by wireless network" in the box where i supposedly have to select my type of wireless security it is blank and i cannot click on it, as i said i think this is a problem with wpa and wpa2

---

### Post by Peter09 on 2011-07-26
OK, go back and click on the network icon and select edit connections.
 
In the box that comes up click the 'wireless' tab.
Delete the access point you are trying to connect to  from the list.
 
Exit the network setup.
 
Now go back and click on the network icon again and try to connect to your network.

---

### Post by Alex715 on 2011-07-26
Ok, so i deleted my connections and tryed again but its still the same thing, ive tried alot of solutions in the last couple of weeks but none of them have worked when i had xp pro installed about 3 weeks ago my wireless worked fine so i dont think its a problem with the hardware, maybe i need a new driver or something?

---

