---
title: "Need some help witj ubuntu 12.04 and hr radeon 6670"
date: 2012-09-04
forum: Hardware
---

### Post by cannon_dt on 2012-09-04
HI,
I just got myself a new hd radeon 6670 and I have installed the latest proprietray catalyst driver and my fglrxinfo shows the following:

```
display: :0.0  screen: 0
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: AMD Radeon HD 6670
OpenGL version string: 4.2.11762 Compatibility Profile Context
```

Now I did a screen capture using ffmpeg and when I ran the output mkv file using vlc, I get the below
```
Your video output acceleration driver does not support the required resolution: 856x509 pixels. The maximum supported resolution is 856x510.
```

I thought I had a good card so why am I getting the below.

For capture I used the below:

ffmpeg -f alsa -ac 2 -i pulse -f x11grab -r 30 \
        -s $(xwininfo -frame | grep -oEe 'geometry [0-9]+x[0-9]+' | grep -oEe '[0-9]+x[0-9]+') \
        -i :0.0+$(xwininfo -frame | grep -oEe 'Corners:\s+\+[0-9]+\+[0-9]+' \
        | grep -oEe '[0-9]+\+[0-9]+' | sed -e 's/\+/,/' ) \
        -acodec pcm_s16le -vcodec libx264 -preset ultrafast -crf 0 -threads 0 \
        -y output.mkv

Can someone help?

Thanks,
Ananth

---

### Post by cannon_dt on 2012-09-06
Can anyone help?

---

