---
title: "Intel 4600 + AMD R9 290 crash after log on screen"
date: 2015-07-27
forum: Hardware
---

### Post by n-hvatov on 2015-07-27
Hello!

My configuration:
Asrock H97 Fatality Perfomance
Intel I7-4770(not K)
32Gb Ram
fresh Ubuntu 14.04/Elementary OS Freya

So I am planning to configure vfio+kvm for passthrough R9 290 to Windows guest OS. And here is my trouble:
When I map an Intel IGX as a primary card in the motherboard bios, I have a crash of lightdm after logging into Unity/Pantheon. After service lightdm restart, I get new logon screen, but then I try to login again this issue appears again. With unity interface I get a flickering logon screen(looks like restarting loop). Last time I tried this configuration I've got something like lightdm exit with status 1 message in the dmesg(I can reproduce this issue and paste a exact message from the log only tomorrow). If Intel IGX disabled(primary card in bios set to Pci-e port) system boot without any issues. Before this setup I had kubuntu 15.04 with a stock kernel(daily updated via official repos) and intel h77 board with a I7-3770 CPU with same discrete card, and there is no problems with booting with both cards(both monitors working with different cards in the same time) 
So now I just use only AMD card and Intel card disabled in bios and I don't know what will happens when I blacklist R9 290 card and will try to load with intel IGX. Please help me with this. Thanks in advance.


Syslog

> Jul 28 10:21:40 grrr-box gnome-session[2097]: WARNING: Error while executing session-migration: Failed to execute child process "session-migration" (No such file or directory)
Jul 28 10:21:40 grrr-box gnome-session[2097]: WARNING: Could not parse desktop file user-dirs-update-gtk.desktop or it references a not found TryExec binary
Jul 28 10:21:40 grrr-box gnome-session[2097]: WARNING: Could not parse desktop file user-dirs-update-gtk-pantheon.desktop or it references a not found TryExec binary
Jul 28 10:21:40 grrr-box rtkit-daemon[1743]: Successfully made thread 2262 of process 2262 (n/a) owned by '1000' high priority at nice level -11.
Jul 28 10:21:40 grrr-box rtkit-daemon[1743]: Supervising 1 threads of 1 processes of 1 users.
Jul 28 10:21:40 grrr-box rtkit-daemon[1743]: Successfully made thread 2266 of process 2262 (n/a) owned by '1000' RT at priority 5.
Jul 28 10:21:40 grrr-box rtkit-daemon[1743]: Supervising 2 threads of 1 processes of 1 users.
Jul 28 10:21:40 grrr-box dbus[773]: [system] Activating service name='org.freedesktop.systemd1' (using servicehelper)
Jul 28 10:21:40 grrr-box dbus[773]: [system] Successfully activated service 'org.freedesktop.systemd1'
Jul 28 10:21:40 grrr-box rtkit-daemon[1743]: Successfully made thread 2275 of process 2262 (n/a) owned by '1000' RT at priority 5.
Jul 28 10:21:40 grrr-box rtkit-daemon[1743]: Supervising 3 threads of 1 processes of 1 users.
Jul 28 10:21:40 grrr-box rtkit-daemon[1743]: Successfully made thread 2276 of process 2262 (n/a) owned by '1000' RT at priority 5.
Jul 28 10:21:40 grrr-box rtkit-daemon[1743]: Supervising 4 threads of 1 processes of 1 users.
Jul 28 10:21:40 grrr-box pulseaudio[2262]: [pulseaudio] x11wrap.c: XOpenDisplay() failed
Jul 28 10:21:40 grrr-box pulseaudio[2262]: [pulseaudio] module.c: Failed to load module "module-x11-publish" (argument: "display=:0"): initialization failed.
Jul 28 10:21:40 grrr-box gnome-session[2097]: Gdk-WARNING: gnome-session: Fatal IO error 4 (Interrupted system call) on X server :0.#012
Jul 28 10:21:40 grrr-box acpid: client 1795[0:0] has disconnected
Jul 28 10:21:40 grrr-box acpid: client connected from 2280[0:0]
Jul 28 10:21:40 grrr-box acpid: 1 client rule loaded
Jul 28 10:22:17 grrr-box gnome-session[2395]: WARNING: Error while executing session-migration: Failed to execute child process "session-migration" (No such file or directory)
Jul 28 10:22:17 grrr-box gnome-session[2395]: WARNING: Could not parse desktop file user-dirs-update-gtk.desktop or it references a not found TryExec binary
Jul 28 10:22:17 grrr-box gnome-session[2395]: WARNING: Could not parse desktop file user-dirs-update-gtk-pantheon.desktop or it references a not found TryExec binary
Jul 28 10:22:17 grrr-box dbus[773]: [system] Activating service name='org.freedesktop.systemd1' (using servicehelper)
Jul 28 10:22:17 grrr-box dbus[773]: [system] Successfully activated service 'org.freedesktop.systemd1'
Jul 28 10:22:17 grrr-box gnome-session[2395]: Gdk-WARNING: gnome-session: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.#012
Jul 28 10:22:17 grrr-box acpid: client 2280[0:0] has disconnected
Jul 28 10:22:17 grrr-box acpid: client connected from 2568[0:0]
Jul 28 10:22:17 grrr-box acpid: 1 client rule loaded
Jul 28 10:22:41 grrr-box acpid: client 2568[0:0] has disconnected
Jul 28 10:22:42 grrr-box acpid: client connected from 2752[0:0]
Jul 28 10:22:42 grrr-box acpid: 1 client rule loaded
Jul 28 10:22:47 grrr-box gnome-session[2838]: WARNING: Error while executing session-migration: Failed to execute child process "session-migration" (No such file or directory)
Jul 28 10:22:47 grrr-box gnome-session[2838]: WARNING: Could not parse desktop file user-dirs-update-gtk.desktop or it references a not found TryExec binary
Jul 28 10:22:47 grrr-box gnome-session[2838]: WARNING: Could not parse desktop file user-dirs-update-gtk-pantheon.desktop or it references a not found TryExec binary
Jul 28 10:22:47 grrr-box rtkit-daemon[1743]: Successfully made thread 3004 of process 3004 (n/a) owned by '1000' high priority at nice level -11.
Jul 28 10:22:47 grrr-box rtkit-daemon[1743]: Supervising 1 threads of 1 processes of 1 users.
Jul 28 10:22:47 grrr-box pulseaudio[3004]: [pulseaudio] pid.c: Stale PID file, overwriting.
Jul 28 10:22:47 grrr-box rtkit-daemon[1743]: Successfully made thread 3006 of process 3004 (n/a) owned by '1000' RT at priority 5.
Jul 28 10:22:47 grrr-box rtkit-daemon[1743]: Supervising 2 threads of 1 processes of 1 users.
Jul 28 10:22:47 grrr-box dbus[773]: [system] Activating service name='org.freedesktop.systemd1' (using servicehelper)
Jul 28 10:22:47 grrr-box dbus[773]: [system] Successfully activated service 'org.freedesktop.systemd1'
Jul 28 10:22:47 grrr-box rtkit-daemon[1743]: Successfully made thread 3013 of process 3004 (n/a) owned by '1000' RT at priority 5.
Jul 28 10:22:47 grrr-box rtkit-daemon[1743]: Supervising 3 threads of 1 processes of 1 users.
Jul 28 10:22:47 grrr-box rtkit-daemon[1743]: Successfully made thread 3014 of process 3004 (n/a) owned by '1000' RT at priority 5.
Jul 28 10:22:47 grrr-box rtkit-daemon[1743]: Supervising 4 threads of 1 processes of 1 users.
Jul 28 10:22:47 grrr-box pulseaudio[3004]: [pulseaudio] x11wrap.c: XOpenDisplay() failed
Jul 28 10:22:47 grrr-box pulseaudio[3004]: [pulseaudio] module.c: Failed to load module "module-x11-publish" (argument: "display=:0"): initialization failed.
Jul 28 10:22:47 grrr-box gnome-session[2838]: Gdk-WARNING: gnome-session: Fatal IO error 4 (Interrupted system call) on X server :0.#012
Jul 28 10:22:47 grrr-box acpid: client 2752[0:0] has disconnected
Jul 28 10:22:47 grrr-box acpid: client connected from 3019[0:0]
Jul 28 10:22:47 grrr-box acpid: 1 client rule loaded

---

