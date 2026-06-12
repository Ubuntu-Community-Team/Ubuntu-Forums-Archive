---
title: "Reg Audio Driver problem in ubuntu 10.04 in Lenovo laptop"
date: 2010-09-02
forum: Hardware
---

### Post by ramanavel on 2010-09-02
Hi,

I have a problem like if i insert my headphones in my laptop socket means i am hearing audio from the laptop speaker as well as in the headphones.

I am using : Ubuntu 10.04 and lenovo G560

Please help me asap.

Thanks & Regards,

Ram

---

### Post by lidex on 2010-09-03
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Enter your user password when prompted. Choose the upload option and provide a link for the output.

---

### Post by tomas4578 on 2012-04-16
> **lidex said:**
> Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Enter your user password when prompted. Choose the upload option and provide a link for the output.

same problem

```
http://www.alsa-project.org/db/?f=1b31f5b4f56a81a53482caf9bf78b9b258101e4f
```

---

