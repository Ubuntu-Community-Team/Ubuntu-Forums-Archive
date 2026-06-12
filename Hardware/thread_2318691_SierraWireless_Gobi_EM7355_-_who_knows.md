---
title: "SierraWireless Gobi EM7355 - who knows?"
date: 2016-03-28
forum: Hardware
---

### Post by p0o9I on 2016-03-28
Hello,
I have problems with getting Gobi EM7355 to work. I don't really know where is the problem or how could I find out. I did some probing (my knowledge is rather limited) and I'm a bit clueless on what to do next.

```

lsusb | grep Sierra
Bus 001 Device 004: ID 1199:901f Sierra Wireless, Inc. 

lsusb -t | grep "Dev 4"
    |__ Port 10: Dev 4, If 12, Class=Communications, Driver=cdc_mbim, 480M
    |__ Port 10: Dev 4, If 13, Class=CDC Data, Driver=cdc_mbim, 480M

```

So the device is loaded, visible and is has some driver. 
As next I found out I can communicate a bit with the device.

```

sudo mbimcli -d /dev/cdc-wdm0 --query-device-caps
[/dev/cdc-wdm0] Device capabilities retrieved:
              Device type: 'embedded'
           Cellular class: 'gsm'
              Voice class: 'no-voice'
                Sim class: 'removable'
               Data class: 'gprs, edge, umts, hsdpa, hsupa, lte, custom'                                      
                 SMS caps: 'pdu-receive, pdu-send'                                                            
                Ctrl caps: 'reg-manual, multi-carrier'                                                        
             Max sessions: '1'                                                                                
        Custom data class: '4G'                                                                               
                Device ID: '351826060245589'                                                                  
            Firmware info: 'SWI9X15C_01.05.11.07'                                                             
            Hardware info: 'EM7355'    

```

I was derping around the mbimcli for a bit and found this suspicious info:

```
sudo mbimcli -d /dev/cdc-wdm0 --query-radio-state                                    
[/dev/cdc-wdm0] Radio state retrieved:                                                                        
             Hardware Radio State: 'on'                                                                       
             Software Radio State: 'off' 

```

And that's is pretty much all what I got. 
I was trying to get the SierraWireless drivers working but I didn't succeed. Maybe I succeeded but the compilation of the drivers did shout some Warnings. Could there be a problem with alias? The driver file (.mod.c) has aliases in it and if I try to resolve them all works fine but not for the device I need.

```
sudo modprobe -R "usb:v1199p9070d*dc*dsc*dp*ic*isc*ip*in*"
qcserial
GobiNet
GobiSerial
sudo modprobe -R "usb:v1199p901fd*dc*dsc*dp*ic*isc*ip*in*"
modprobe: FATAL: Module usb:v1199p901fd*dc*dsc*dp*ic*isc*ip*in* not found.

```

I didnt find /etc/modprobe.conf in which I could set the alias. So I  created it. Didnt work. I moved it to /etc/modprobe.d/ and nothing  changed.
Therefore I cant debug the thing with tools from SierraW as  they work only with their drivers which I didn't make to load on boot  and so on..

Does anybody know what could I do?
Thank you very much.

---

