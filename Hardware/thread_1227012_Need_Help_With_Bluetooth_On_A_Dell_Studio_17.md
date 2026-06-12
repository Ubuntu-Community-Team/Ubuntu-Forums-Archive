---
title: "Need Help With Bluetooth On A Dell Studio 17"
date: 2009-07-30
forum: Hardware
---

### Post by twistedtrichrome on 2009-07-30
Hi, I'm totally new to Ubuntu/Kubuntu just been using it for a few weeks now and am starting to figure things out.Recently I read that you can connect a ps3 sixaxis dualshock 3 controller via bluetooth to play emulated consoles.I am currently runnin Kubuntu 9.04 (Jaunty) on a Dell Studio 17 laptop with on board blue tooth but am having trouble telling if my blue tooth is enabled. (following instructions from a site ([https://help.ubuntu.com/community/Sixaxis](https://help.ubuntu.com/community/Sixaxis)) after inputing the code to run sixpair (as follows) 

c) Run sixpair $ sudo ./sixpair
    sixpair will echo
   Current Bluetooth master: xx : xx : xx : xx : xx : xx
   Setting master bd_addr to xx : xx : xx : xx : xx : xx

I get this message,
user@hostname:~/Documents$ gcc -o sixpair sixpair.c -lusb
user@hostname:~/Documents$ sudo ./sixpair
Current Bluetooth master: 00:1a:80:2d:6e:0f
Unable to retrieve local bd_addr from `hcitool dev`.
Please enable Bluetooth or specify an address manually.
user@hostname:~/Documents$ 
user@hostname:~/Documents$ sixpair will echo
bash: sixpair: command not found
user@hostname:~/Documents$ Current Bluetooth master: xx : xx : xx : xx : xx : xx
bash: Current: command not found
user@hostname:~/Documents$ Setting master bd_addr to xx : xx : xx : xx : xx : xx
bash: Setting: command not found

also the bluetooth indicator light on the laptop is not lit up nor is there an icon in the taskbar.(Note) I dont know if its related but there is an application called kdebluetooth4 under applications>internet,but when i click it nothing happens.I'm totally confused if anyone could help me try and diagnose my problem id be very greatful
thanks again
  
                            (Stewie)

---

### Post by doggyollie on 2012-02-23
I had this same problem when trying to connect to my phone.

If you know the address that you would like to change it to use this command in terminal
  ```
sudo ./sixpair XX:XX:XX:XX:XX:XX
```where "XX:XX:XX:XX:XX:XX" is blue tooth address of [B]the device that you are trying connect the controller to.

[/B]All thanks to [dbzfanatic ]("http://forum.xda-developers.com/member.php?u=2677253")on xda
[http://forum.xda-developers.com/showthread.php?t=1179929&page=21](http://forum.xda-developers.com/showthread.php?t=1179929&page=21)

---

