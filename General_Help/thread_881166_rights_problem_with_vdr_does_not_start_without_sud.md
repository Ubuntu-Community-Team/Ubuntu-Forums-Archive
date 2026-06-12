---
title: "rights problem with vdr does not start without sudo"
date: 2008-08-05
forum: General Help
---

### Post by ~~MAINFRAIME²~~ on 2008-08-05
I'm using mythbuntu 8.04 and I have installed vdr 1.6 with xineliboutput and some plug-ins but I don't get it to run at start up.

When I start it manually "sudo /etc/init.d/vdr restart" it starts and works but without sudo I always have some errors.

```

mythbox1@mythbox1-desktop:~$ /etc/init.d/vdr restart
Restarting Linux Video Disk Recorder: vdr - seems not to be running
Searching for plugins (VDR 1.6.0-1/1.6.0) (cache hit): xineliboutput chanorg femon epgsearch quickepgsearch epgsearchonly conflictcheckonly wirbelscanstart-stop-daemon: Unable to open pidfile `/var/run/runvdr.pid' for writing: Permission denied (Permission denied)
.

```

And if I run "runvdr" I get these errors
```

chmod: changing permissions of `/dev/input/event0': Operation not permitted
chmod: changing permissions of `/dev/input/event1': Operation not permitted
chmod: changing permissions of `/dev/input/event2': Operation not permitted
chmod: changing permissions of `/dev/input/event3': Operation not permitted
chmod: changing permissions of `/dev/input/event4': Operation not permitted
chmod: changing permissions of `/dev/input/event5': Operation not permitted

```

I changed "var/run/runvdr.pid" to vdr as group with read/write permission.
and also tried to set "/dev/input" to 777 but this does not fix the problem.

How do I get vdr to start without sudo so I can start it at start up?

---

### Post by DagMan on 2008-08-06
/etc/init.d/vdr will have to be started stopped, and restarted as the root user or using sudo. 

Scripts in that location usually run at boot.  What is the scenario, that it isn't running at boot, either it doesn't run at all or fails, or that you have it set up not to run at boot and want to launch it when you need it?

---

### Post by ~~MAINFRAIME²~~ on 2008-08-07
It's setup to start automatically but then fails here is the sys log entry
```

Aug  8 04:16:34 mythbox1-desktop vdr: [6093] [xine..put] load_frontend: entry at 0x7fe3cb6e1140
Aug  8 04:16:34 mythbox1-desktop vdr: [6093] [xine..put] Using frontend sxfe (X11 (sxfe)) from libxineliboutput-sxfe.so.1.0.1
Aug  8 04:16:34 mythbox1-desktop vdr: [6093] [xine..put] cXinelibLocal::Action - fe created
Aug  8 04:16:34 mythbox1-desktop vdr: [6093] [xine..put] keypress_handler(): X11 Keyboard disabled in config
Aug  8 04:16:34 mythbox1-desktop vdr: [6093] [vdr-fe]    sxfe_display_open(width=720, height=576, fullscreen=1, display=0.0)
Aug  8 04:16:34 mythbox1-desktop vdr: [6093] [vdr-fe]    sxfe_display_open: failed to connect to X server (0.0)
Aug  8 04:16:34 mythbox1-desktop vdr: [6093] [vdr-fe]       (ERROR (xine_sxfe_frontend.c,873): No such file or directory)
Aug  8 04:16:34 mythbox1-desktop vdr: [6093] [vdr-fe]    sxfe_display_open: failed to connect to X server (:0.0)
Aug  8 04:16:34 mythbox1-desktop vdr: [6093] [vdr-fe]       (ERROR (xine_sxfe_frontend.c,885): No such file or directory)
Aug  8 04:16:34 mythbox1-desktop vdr: [6093] [vdr-fe]    sxfe_display_open: failed to connect to X server (127.0.0.1:0.0
Aug  8 04:16:34 mythbox1-desktop vdr: [6093] [vdr-fe]       (ERROR (xine_sxfe_frontend.c,889): Connection refused)
Aug  8 04:16:34 mythbox1-desktop vdr: [6093] [vdr-fe]    sxfe_display_open: failed to connect to X server.
Aug  8 04:16:34 mythbox1-desktop vdr: [6093] [vdr-fe]       (ERROR (xine_sxfe_frontend.c,892): Connection refused)
Aug  8 04:16:34 mythbox1-desktop vdr: [6093] [vdr-fe]    If X server is running, try running "xhost +" in xterm window
Aug  8 04:16:34 mythbox1-desktop vdr: [6093] [xine..put] cXinelibLocal: Error initializing display
Aug  8 04:16:34 mythbox1-desktop vdr: [6093] [xine..put] cXinelibLocal::Action: thread finished
Aug  8 04:16:34 mythbox1-desktop vdr: [6093] Local decoder/display (cXinelibThread) thread ended (pid=5908, tid=6093)
Aug  8 04:16:34 mythbox1-desktop vdr: [5908] [xine..put] cXinelibDevice::Start(): Local frontend init failed
Aug  8 04:16:34 mythbox1-desktop vdr: [5908] [xine..put] cXinelibOsdProvider: shutting down !
Aug  8 04:16:34 mythbox1-desktop vdr: [6091] section handler thread ended (pid=5908, tid=6091)
Aug  8 04:16:34 mythbox1-desktop vdr: [6090] tuner on device 1 thread ended (pid=5908, tid=6090)
Aug  8 04:16:34 mythbox1-desktop vdr: [5908] [xine..put] cXinelibDevice::StopDevice(): Stopping device ...
Aug  8 04:16:35 mythbox1-desktop vdr: [6094] Remote decoder/display server (cXinelibServer) thread ended (pid=5908, tid=6094)
Aug  8 04:16:35 mythbox1-desktop vdr: [5908] deleting plugin: wirbelscan
Aug  8 04:16:35 mythbox1-desktop vdr: [5908] deleting plugin: conflictcheckonly
Aug  8 04:16:35 mythbox1-desktop vdr: [5908] deleting plugin: epgsearchonly
Aug  8 04:16:35 mythbox1-desktop vdr: [5908] deleting plugin: quickepgsearch
Aug  8 04:16:35 mythbox1-desktop vdr: [5908] deleting plugin: epgsearch
Aug  8 04:16:35 mythbox1-desktop vdr: [5908] deleting plugin: femon
Aug  8 04:16:35 mythbox1-desktop vdr: [5908] deleting plugin: chanorg
Aug  8 04:16:35 mythbox1-desktop vdr: [5908] deleting plugin: xineliboutput
Aug  8 04:16:35 mythbox1-desktop vdr: [5908] max. latency time 0 seconds
Aug  8 04:16:35 mythbox1-desktop vdr: [5908] exiting, exit code 2
Aug  8 04:16:35 mythbox1-desktop runvdr: stopping after fatal fail ()

```

So I have put "xhost +" in a script at ~/.config/autostart and then I try to start vdr which is not working without sudo.
I want to use my PC on a CRT TV and playing with the console isn't funny there.

---

