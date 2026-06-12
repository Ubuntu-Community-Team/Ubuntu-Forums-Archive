---
title: "AMD gpu not in use"
date: 2022-11-27
forum: Hardware
---

### Post by colelehl on 2022-11-27
So I've had this laptop for a while, and I quite like it. Although neofetch tells me I have an AMD gpu, every game and software uses the cpu graphics. I've tried installing the AMD software, and other things but I have no idea how I can use it. When I use the command lspci -k | grep -EA2 'VGA|3D' it only shows my intel graphics. Can somebody help me figure out how to use my gpu as well as why this is happening?

---

### Post by mIk3_08 on 2022-11-28
Please run the script on this give url page below and post the information or pastebin link in this thread. Regards and cheers.
Code:
[https://github.com/UbuntuForums/system-info](https://github.com/UbuntuForums/system-info)
Or
Just run the script/command below in your terminal:
```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/system-info/raw/main/system-info && \
chmod +x system-info && \
./system-info
```

---

