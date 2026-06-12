---
title: "Ubuntu on NC8000"
date: 2010-01-03
forum: Hardware
---

### Post by Milambar on 2010-01-03
I successfully installed Ubuntu 9.10 on a HP nc8000 "Business Notebook", with 2GB ram and 100GB hdd. 

Everything works "out of the box", even the onboard WIFI. Kudos to the Linux community and Ubuntu developers for this. The install took 30 minutes, including burning the cd (for downloading it too, add 10 minutes extra).

Now a question. I have been trying to get configure Conky, specifically get my CPU and GPU temperatures. In /proc/acpi/thermal_zone there are 3 sub directories, TZ1, TZ2, and TZ3. Inside each is a file called "temperature", and each file contains a different value.

How do I find out which one relates to the CPU and which one relates to the GPU, and presumably the third is the hdd or mobo temp?

---

