---
title: "HP Officejet 6962 prints one copy"
date: 2021-08-01
forum: Hardware
---

### Post by ishwashere on 2021-08-01
I have Ubuntu 20.04 install on a Dell XPS 9500 laptop. My HP Officejet 6962 only prints one copy in the selection of multiple. I am a novice to linux. Any help would be appreciated.

---

### Post by brian_p on 2021-08-01
You will have a PPD for the printer in etc/cups/ppd. Get its name. I will call it HP_PPD. You substitute the correct filename, of course.

Give the outputs of 

```
sudo grep "PCFileName" /etc/cups/ppd/HP_PPD
```
```
sudo grep "NickName" /etc/cups/ppd/HP_PPD
```
```
sudo grep "cupsManualCopies" /etc/cups/ppd/HP_PPD
```

---

### Post by ishwashere on 2021-08-01
[https://www.dropbox.com/s/10kdw4r7a3exhiv/Screenshot%20from%202021-08-01%2018-16-37.png?dl=0](https://www.dropbox.com/s/10kdw4r7a3exhiv/Screenshot%20from%202021-08-01%2018-16-37.png?dl=0) 
I typed in the commands but I was not able to print multiple copies.

---

### Post by brian_p on 2021-08-02
The issue is a bug in cups-filters, fixed in a later version. Edit the PPD to have

```
*cupsManualCopies: True
```

---

### Post by ishwashere on 2021-08-02
How do I edit the PPD file? Terminal or Can I use a text editor app?

---

### Post by brian_p on 2021-08-02
> **ishwashere said:**
> How do I edit the PPD file? Terminal or Can I use a text editor app?

I would use the terminal ```
sudo nano FILE
``` perhaps. A text editor app is OK, provided it has root privileges.

---

### Post by ishwashere on 2021-08-03
[IMG]https://www.dropbox.com/s/yc38g92v5y174q6/Screenshot%20from%202021-08-03%2005-47-28.png?dl=0[/IMG]

I edited the .ppd with no results. With increased copies the result is still one page.

---

### Post by brian_p on 2021-08-03
You edited *true* to be *True*? Restart CUPS?

---

