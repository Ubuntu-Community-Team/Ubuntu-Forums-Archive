---
title: "External monitor goes blank after reboot in Ubuntu 8.10"
date: 2008-11-01
forum: Hardware
---

### Post by mjschmidt on 2008-11-01
I have installed 8.10 on my toshiba laptop using Wubi (on a Vista Home Premium machine). I have a Samsung 22" (T220) external monitor attached to the laptop via VGA cable.

I have successfully set up the external monitor as an extended display. When I boot the computer into Ubuntu it works fine.

Problem: if I REBOOT Ubuntu into Unbuntu, the external monitor goes a very light beige colour, while the laptop monitor loads the wallpaper normally. Because my external monitor is set up as the main monitor, I can not click any menus or applications.

In order to get both screens working again I have to hold down the power button on my laptop to turn it off, then unplug the second monitor, plug it back in, wait a bit, then boot my machine into Ubuntu again.

Any ideas?

---

### Post by wadd0001 on 2008-11-06
for future reference you can just restart your session by CTRL+ALT+BACKSPACE, also CTRL+F1 will start another session so you don't have to manually reboot

post the output of typing xrandr in the terminal and we can try to fix this

---

### Post by gyterpena on 2008-11-20
Same over here. 


kernel: [ 8002.132101] CE: hpet increasing min_delta_ns to 15000 nsec
console-kit-daemon[5170]: WARNING: Unable to activate console: No such device or address
gdm[5438]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0
bonobo-activation-server (peter-13447): could not associate with desktop session: Failed to connect to socket /tmp/dbus-quGCDn5fwh: Connection refu$
acpid: client connected from 13541[0:0]
gdmgreeter[13565]: Gtk-WARNING: Unable to locate theme engine in module_path: "ubuntulooks",
pulseaudio[13675]: ltdl-bind-now.c: Failed to find original dlopen loader.
pulseaudio[13678]: pid.c: Stale PID file, overwriting.
pulseaudio[13678]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
pulseaudio[13678]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
pulseaudio[13738]: ltdl-bind-now.c: Failed to find original dlopen loader.
pulseaudio[13738]: pid.c: Daemon already running.
pulseaudio[13738]: main.c: pa_pid_file_create() failed.
pulseaudio[13678]: module-x11-xsmp.c: X11 session manager not running.
pulseaudio[13678]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.

---

