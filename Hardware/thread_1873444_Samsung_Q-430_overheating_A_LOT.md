---
title: "Samsung Q-430 overheating A LOT"
date: 2011-11-01
forum: Hardware
---

### Post by rugbert on 2011-11-01
So my laptop has started overheating a LOT and Im not sure why. Ive been using ubuntu on it for years and I feel like it didnt start overheating really until I upgraded to 11.04. 

and even when I installed 10.10 from scratch it still overheats. At first I thought it was just when I had my second monitor plugged in (and then when I was playing flash videos which is what usually shutdown my laptop) but no, it just turned off on me and Im not using it. I used to be able to run TONS of stuff (virtual box, chrome and  firefox (with multiple tabs), rails server, gedit, and pandora) but now it seems to overheat ALL THE TIME. Im wondering now if it could be a hardware issue tho.

I mean, look art my syslogs
```

ov  1 11:25:14 samsung kernel: [55350.875494] intel ips 0000:00:1f.6: MCP limit exceeded: Avg temp 9125, limit 9000
Nov  1 11:25:19 samsung kernel: [55355.867188] intel ips 0000:00:1f.6: MCP limit exceeded: Avg temp 9760, limit 9000
Nov  1 11:25:24 samsung kernel: [55360.858860] intel ips 0000:00:1f.6: MCP limit exceeded: Avg temp 10035, limit 9000
Nov  1 11:25:29 samsung kernel: [55365.850539] intel ips 0000:00:1f.6: MCP limit exceeded: Avg temp 9940, limit 9000
Nov  1 11:25:34 samsung kernel: [55370.842230] intel ips 0000:00:1f.6: MCP limit exceeded: Avg temp 10080, limit 9000
Nov  1 11:28:59 samsung kernel: [55575.501270] intel ips 0000:00:1f.6: MCP limit exceeded: Avg temp 9246, limit 9000
Nov  1 11:29:04 samsung kernel: [55580.492928] intel ips 0000:00:1f.6: MCP limit exceeded: Avg temp 9331, limit 9000
Nov  1 11:29:09 samsung kernel: [55585.484628] intel ips 0000:00:1f.6: MCP limit exceeded: Avg temp 9396, limit 9000
Nov  1 11:29:34 samsung kernel: [55610.443024] intel ips 0000:00:1f.6: MCP limit exceeded: Avg temp 9996, limit 9000
Nov  1 11:29:39 samsung kernel: [55615.434705] intel ips 0000:00:1f.6: MCP limit exceeded: Avg temp 9962, limit 9000
Nov  1 11:29:44 samsung kernel: [55620.426388] intel ips 0000:00:1f.6: MCP limit exceeded: Avg temp 10088, limit 9000
Nov  1 11:29:49 samsung kernel: [55625.418077] intel ips 0000:00:1f.6: MCP limit exceeded: Avg temp 10140, limit 9000
Nov  1 11:29:50 samsung kernel: [55626.671789] Critical temperature reached (103 C), shutting down.

```

Anyone have any advice?

---

### Post by diasf on 2011-11-01
First of all, are you sure the coolers are spinning and the system itself is clear of dust and etc?

---

### Post by Lars Noodén on 2011-11-01
I'm seeing a similar problem.  

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/881593](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/881593)

Is the fan running while it overheats?

---

### Post by rugbert on 2011-11-02
I opened it up and air dusted it and it SEEMS to have fixed the issue a bit more but it still tends to heat up quickly.

Im not sure if the fans were spinning when it was overheating, Im usually listening to music so I hadnt noticed.

---

### Post by Devnox on 2011-11-06
I am having the same problem with my ASUS ul80 laptop and recently my friend who was using ubuntu on his laptops hard drive melted and I am now afraid for mine. It used to just shut down when it overheated so i put fans under it and that keeps it at about 160 to 170 with the fans running. It has always run fine with windows 7 and there is no dust in it to speak of.

---

### Post by diasf on 2011-11-07
> **Devnox said:**
> I am having the same problem with my ASUS ul80 laptop and recently my friend who was using ubuntu on his laptops hard drive melted and I am now afraid for mine. It used to just shut down when it overheated so i put fans under it and that keeps it at about 160 to 170 with the fans running. It has always run fine with windows 7 and there is no dust in it to speak of.

Install and configure cpufreqd.... your processor is probably always on the highest frequency. Also, make sure you use the "ondemand" governor.... that will help

---

