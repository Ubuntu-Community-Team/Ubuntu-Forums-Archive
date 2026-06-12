---
title: "Ubuntu wireless doesn't work and stopped it from working in windows as welll"
date: 2012-03-21
forum: Hardware
---

### Post by detroitdiesel on 2012-03-21
I installed Ubuntu on my Lenovo b575 laptop with windows 7. Wireless did not work until I typed "rmmod -f aver-wmi" but it only worked temporally. After I did this though, I typed in 
Code:
sudo su
echo "blacklist acer-wmi" >> /etc/modprobe.d/blacklist.conf
exit

To try and make it permmanant. I then restarted, and there was no wireless there, and I typed in  the "rmmod -f acer-wmi" and it said it could not find the file, and wireless would not turn on at all this time. 

I have now uninstalled ubuntu. I plan on trying to reinstalling ubuntu and trying again. Is there anything additional i should try. 

Please note i am a linux newbie. Thanks.

---

### Post by WinRiddance on 2012-03-21
If you perform a clean installation with Ubuntu the wireless network (wifi) normally works by default ... assuming that the wireless on/off switch on your laptop is switched to on. If it doesn't work by default then it's usually because the network has a password protected firewall. I know this to be the case with roadrunner, ATT, and most other major providers. So you'd have to click on the wifi icon within Ubuntu to edit or add wifi settings ... normally you'd only need to click on CONNECT which should then prompt you for a wep or wap2 password.

**Scenario 2** ... If you can tell that your wifi is trying to work but just can't keep the connection alive for any length of time, try to see what happens if you use an external wifi USB adapter/stick. I always keep one handy because sometimes Linux/Ubuntu behaves a little quirky with wifi settings initially. Of course a direct cable connection to your Internet router should always work by default ...
[B]
Scenario 3[/B] ... Last but not least, if you do get a connection working somehow but your wifi is still being buggy, you can also try to install WICD from the software center. It's another network manager that seems to work better on some computers. But to get WICD working properly and by default, you'll want to get into your SYSTEM ... STARTUP APPLICATIONS ... in order to disable the default network manager, followed by making sure that WICD is enabled instead. Restart the system and hopefully all will be fine.
Sorry, but that's all of my limited Linux/Wfi knowledge ... 

**Whoops, forgot to mention** ... If your wifi stopped working in Windows too, then it's not related to Linux or your computer hardware. The only logical explanation for your wireless to stop working in both environments, Linux/Ubuntu as well as Windows, is for the problem to be at the router or cable modem end which would then indicate a problem with your Internet access provider. I've used Windows professionally for 18 years and I've never seen a previously working Windows wifi environment suddenly stop working ... unless it was related to router/modem problems from the access provider ...

.

---

### Post by ActionParsnip on 2012-05-01
I asked you a question in IRC, you didn't reply. Who is at fault? You failed to reply to my question then you retort with:

(13:57:53) w3333: f it

How the hell can anyone help you when you fail to provide responces to basic questions.

Think about it.....

---

