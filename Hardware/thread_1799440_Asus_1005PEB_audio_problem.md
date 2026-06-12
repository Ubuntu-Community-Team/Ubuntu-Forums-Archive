---
title: "Asus 1005PEB audio problem"
date: 2011-07-07
forum: Hardware
---

### Post by Venality on 2011-07-07
My brothers HDD crashed, Since windows is expensive I put ubuntu on it. The only problem is there is no sound at all. So what are some ways to help me troubleshoot and find out what exactly is going on with it?

---

### Post by lidex on 2011-07-07
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

