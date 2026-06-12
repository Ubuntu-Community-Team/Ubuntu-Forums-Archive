---
title: "Help! r8168 ethernet driver does not support kernel 2.6.24!"
date: 2008-10-18
forum: General Help
---

### Post by gausie on 2008-10-18
Driver: [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false)

When I run **make clean modules**, I get this

> make[2]: Entering directory `/usr/src/linux-headers-2.6.24-21-generic'
scripts/Makefile.build:41: /src/Makefile: No such file or directory


I know this to imply that the driver's not compatible with my kernel, but how can I fix this?

Thanks

Gausie

---

### Post by shawnrgr on 2008-10-19
Im not positive but from what i've heard Intrepid fixed TONS of wifi card driver issues. Especially the realtek drivers.

---

### Post by gausie on 2008-10-19
Yea I've heard this too. Is there any way of using the fixes without changing operating system. I'm not comfortable with changing over completely as a main OS - is that justified?

Gausie

---

### Post by shawnrgr on 2008-10-19
I think a lot of it has to do with the kernel interpid is using. you could try compiling the kernel source from intrepid... but thats a little beyond me. There might be easier ways to accomplish this. Im sure someone else here knows

---

