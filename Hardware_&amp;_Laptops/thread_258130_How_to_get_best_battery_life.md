---
title: "How to get best battery life?"
date: 2006-09-15
forum: Hardware &amp; Laptops
---

### Post by stbaker on 2006-09-15
Hello,

I recently bought a Lenovo T60 (1.83 core duo, ati 1300, 512 MB, etc.) I'm a huge fan of ubuntu, but sadly it only gave me a typical battery life of ~ 3 hrs. In windows and suse 10.1, I usually get ~ 4 hrs. The only big discernable difference between the way ubuntu manages power compared to suse is that suse uses powersaved, which conflicts with ubuntu's default packages.

So my question is, what have people done with ubuntu to maximize battery life? Is there a convenient way to use powersave with ubuntu? And does it look like edgy will give us bettery battery life?

Thanks,

Sean

---

### Post by mariux on 2006-09-15
1. Make speedstep work and set it to "battery" mode
2. Clock down your gpu ("rovclock" for ati)
3. Undervolt your cpu (google for "undervolt gentoo wiki")

---

### Post by stbaker on 2006-09-15
I have the speedstep stuff working, and I've fiddled with ATI's powerplay (I can't use rovclock, because the native radeon driver doesn't support my card yet). However, I'm still not getting the battery life that windows / suse give me. Is undervolting the CPU's safe? I have a lot of experience in circuit / processor design, and designers certainly make sure their design works at low voltages, but it isn't always the best thing for them. Anyone else doing this with the core duos and having success?

---

### Post by mariux on 2006-09-16
Yes its safe, your computer might crash but its not going to break.

---

### Post by Melcar on 2006-09-16
I installed and applet called emifreq-applet which lets you underclock your CPU.

---

