---
title: "Does Ubuntu12.04 Nouveau driver implement Optimus laptop"
date: 2012-05-31
forum: Hardware
---

### Post by jao_madn on 2012-05-31
Hi Gud day,

I would like to ask about if someone out here use an optimus technology laptop install the bumblebee package to enable to use the nvidia graphics card.

I just wondering on my optimus laptop which i install the latest ubuntu dist. which is 12.04 precise and update to kernel as of this date is 3.2.0-24.
Im using lucyd and bumblebee to access my paid graphics nvidia card. Before no bumblebee package install i can't use google-earth
or so called webgl on a browser. In my understanding the intel card can't handle high end application that required a high end card which is the purpose of the
nvidia. with bumblebee installed google-earth and webgl is a piece of cake. an any application that required  extensive graphics. Now im confused since the default
installation of the precise 12.04 as of 2012-06-01, the google earth and webgl works fine, so does it mean the default install driver can used the nvidia or access the nvidia card.
Question:

1. I never found nvidia module/driver loaded when i run google-earth not like the bumblebee "optirun <apps>" so therefore what driver is the apps using?
2. Does the nouveau driver can access or used the nvidia card ( nouveau driver is opensource driver for nvidia right )
3. On the nouveau official website, its states that Optirun technology is not implemented yet. then maybe im wrong thinking nouveau driver is using the nvidia card?

Thanks And Best Regards.

---

### Post by seenthelite on 2012-06-12
When you have got it running by using optirun (command), do this in the terminal

```
lshw
```

and you will see something like:- configuration: driver=nvidia or nouveau

---

