---
title: "Hou to get HP laptops work with Ubuntu WIFI"
date: 2012-02-27
forum: Hardware
---

### Post by Jayhawker on 2012-02-27
I have two HP computers: a laptop and a notebook. None of them can work with my WIFI in Ubuntu 11/10. 

Curioysly, it seems they detect other routers, but the open ones don't really work either. Mine is not even detected.

Do you know how to solve the problem?

Thanks a lot

---

### Post by kc1di on 2012-02-27
If you could supply a little more information we may be able to help
What model of HP?  do you know the wireless card being used?

Did you install any drivers?

---

### Post by SeijiSensei on 2012-02-27
Also what type of encryption are you using?  I've had the best success with WPA2, which also happens to be the most secure option as well.

---

### Post by Jayhawker on 2012-02-27
I have an HP pavilion dv6500 and an HP notebook Mini 110 1146ss. The WiFI is a usual one 802.1, 128 bits WEP.

There is the driver UBUNTU facilitates: STA Broadcom, and netrtlxp.

Wireless works well when in Windows.

Thanks

---

### Post by kc1di on 2012-02-27
> **Jayhawker said:**
> I have an HP pavilion dv6500 and an HP notebook Mini 110 1146ss. The WiFI is a usual one 802.1, 128 bits WEP.

There is the driver UBUNTU facilitates: STA Broadcom, and netrtlxp.

Wireless works well when in Windows.

Thanks
You should got to system settings >additional drivers> and select the recommended driver and install it. I have the same card as yours and it work fine on my laptop. 

It should be broadcom current.

---

### Post by Jayhawker on 2012-02-28
Thanks, but as I said, this driver is already installed. What can be the problem?


> **kc1di said:**
> You should got to system settings >additional drivers> and select the recommended driver and install it. I have the same card as yours and it work fine on my laptop. 

It should be broadcom current.

---

### Post by kc1di on 2012-03-08
> **Jayhawker said:**
> Thanks, but as I said, this driver is already installed. What can be the problem?

Sorry took so long to get back to you.  Was away on business and could not get to the forum. 

Did you ever get it working?
when you go to the additional drivers screen is there more than one driver available and did you install the recommended one?

---

### Post by Jayhawker on 2012-03-12
Thanks for your concern.

No. It has never worked.

Yes, I have installed the recommended one; no other driver available. 

I begin to suspect that maybe Ubuntu Linux only works with WPA/WPA2. My router is a 128 bits WEP.

I think it because I can surf without any problem with other routers (library, coffee shops) that maybe are WPA/WPA2

Am I right?

If so, how to solve it, please?  



> **kc1di said:**
> Sorry took so long to get back to you.  Was away on business and could not get to the forum. 

Did you ever get it working?
when you go to the additional drivers screen is there more than one driver available and did you install the recommended one?

---

### Post by Yellow Pasque on 2012-03-12
Did you try disabling the password on your router to see if that's the cause?

---

### Post by coffeecat on 2012-03-12
@Jayhawker, I have a HP mini 110 with the Broadcom BCM4313 wireless card, and this works well enough for me with the default brcmsmac open-source driver, but I get a stronger signal with the STA driver. This is in Oneiric/11.10. However, there is a bug with the STA driver installer in Oneiric and there is one other step you have to take (for the BCM4313 card) before it will work. Before I give you this, we need to confirm which Broadcom wireless card you are using. Post the output of this terminal command:

```
lspci -vvnn | grep 14e4
``` 

(That's a numeric 1 in 14e4.)

This doesn't tell us enough:

> **Jayhawker said:**
>  The WiFI is a usual one 802.1, 128 bits WEP.


---

