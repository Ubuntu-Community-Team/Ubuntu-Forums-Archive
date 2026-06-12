---
title: "New Problem with CPU Scaling"
date: 2009-02-09
forum: Hardware
---

### Post by simplyai on 2009-02-09
Yes, I have a new problem. Before it said that CPU frequency scaling was unsupported and then I browsed the forums and found a link to this:

[http://technowizah.com/2007/01/debian-how-to-cpu-frequency-management.html]("http://technowizah.com/2007/01/debian-how-to-cpu-frequency-management.html")

I followed the steps, everything worked. And then I reboot my laptop and then when I try to scale it to powersave mode, it doesn't do anything, it stays on performance mode....

Uhh, help please?

---

### Post by Yashiro on 2009-02-10
You could run
*sudo dpkg-reconfigure gnome-applets*
then install the gnome power scaling applet onto your panel.

OR implement the changes mentioned at the bottom of that tutorial correctly.

---

### Post by HavocXphere on 2009-02-10
Not directly helping, but I found this yesterday: You can check available frequencies and the current frequency via:
> havoc@Sphere:~$ cat /sys/devices/system/cpu/cpu0/cpufreq/**scaling_available_frequencies**
2331000 1998000
havoc@Sphere:~$ sudo cat /sys/devices/system/cpu/cpu0/cpufreq/**cpuinfo_cur_freq**
1998000

---

### Post by linux_tech on 2009-02-10
I'm not sure how you are implementing it, by applet or command. Here are a few helpful links that explain how to implement it by command.

[http://ubuntu.wordpress.com/2005/11/04/enabling-cpu-frequency-scaling/](http://ubuntu.wordpress.com/2005/11/04/enabling-cpu-frequency-scaling/)
[http://ubuntuforums.org/showthread.php?t=248867](http://ubuntuforums.org/showthread.php?t=248867)

---

### Post by simplyai on 2009-02-10
I followed what the links to what linux_tech put up and still everything happened.

---

