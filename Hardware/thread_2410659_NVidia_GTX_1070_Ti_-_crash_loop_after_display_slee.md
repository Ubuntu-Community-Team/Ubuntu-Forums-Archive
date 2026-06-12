---
title: "NVidia GTX 1070 Ti - crash loop after display sleeps with fresh install"
date: 2019-01-18
forum: Hardware
---

### Post by duckyduckyducky on 2019-01-18
Good morning,

I'm having issues running a fresh install of Ubuntu 18.04.1 on an HP z800 workstation.

Configuration:
- HP z800 w/ 2x Xeon X5680
- NVidia GTX 1070 Ti GPU (known good)
- 3 monitors
- Installed NVidia 390 drivers via Software & Upgrades "Additional Drivers" pane - installed and worked with one click.

The issue I am experiencing is that any time the computer tries to let the displays sleep they end up in a disconnect/reconnect loop and the machine is unrecoverable until I hard reset it.  One of the three screens constantly shuts off and turns on again, showing only a blank screen with a cursor, and the other two displays remain off.  This is a major issue for me, since it means I can't lock my computer without it crashing.

I'm including a sample of my Xorg.log output below.  It appears to generate these errors in a loop during the failure condition.  Happy to provide additional logs if they would be helpful.  I didn't see anything in syslog during the periods when this is taking place.

Thanks!

```
[ 60884.570] (--) NVIDIA(GPU-0): DFP-3: disconnected[ 60884.570] (--) NVIDIA(GPU-0): DFP-3: Internal TMDS
[ 60884.570] (--) NVIDIA(GPU-0): DFP-3: 600.0 MHz maximum pixel clock
[ 60884.570] (--) NVIDIA(GPU-0): 
[ 60884.603] (--) NVIDIA(GPU-0): Ancor Communications Inc ASUS VS239 (DFP-0): connected
[ 60884.603] (--) NVIDIA(GPU-0): Ancor Communications Inc ASUS VS239 (DFP-0): Internal TMDS
[ 60884.603] (--) NVIDIA(GPU-0): Ancor Communications Inc ASUS VS239 (DFP-0): 600.0 MHz maximum pixel clock
[ 60884.603] (--) NVIDIA(GPU-0): 
[ 60884.619] (--) NVIDIA(GPU-0): Ancor Communications Inc ASUS VS239 (DFP-1): connected
[ 60884.619] (--) NVIDIA(GPU-0): Ancor Communications Inc ASUS VS239 (DFP-1): Internal TMDS
[ 60884.619] (--) NVIDIA(GPU-0): Ancor Communications Inc ASUS VS239 (DFP-1): 165.0 MHz maximum pixel clock
[ 60884.619] (--) NVIDIA(GPU-0): 
[ 60884.619] (--) NVIDIA(GPU-0): DFP-2: disconnected
[ 60884.619] (--) NVIDIA(GPU-0): DFP-2: Internal DisplayPort
[ 60884.619] (--) NVIDIA(GPU-0): DFP-2: 1440.0 MHz maximum pixel clock
[ 60884.619] (--) NVIDIA(GPU-0): 
[ 60884.626] (--) NVIDIA(GPU-0): DFP-3: disconnected
[ 60884.626] (--) NVIDIA(GPU-0): DFP-3: Internal TMDS
[ 60884.626] (--) NVIDIA(GPU-0): DFP-3: 600.0 MHz maximum pixel clock
[ 60884.626] (--) NVIDIA(GPU-0): 
[ 60884.626] (--) NVIDIA(GPU-0): DFP-4: disconnected
[ 60884.626] (--) NVIDIA(GPU-0): DFP-4: Internal DisplayPort
[ 60884.626] (--) NVIDIA(GPU-0): DFP-4: 1440.0 MHz maximum pixel clock
[ 60884.626] (--) NVIDIA(GPU-0): 
[ 60884.626] (--) NVIDIA(GPU-0): DFP-5: disconnected
[ 60884.626] (--) NVIDIA(GPU-0): DFP-5: Internal TMDS
[ 60884.626] (--) NVIDIA(GPU-0): DFP-5: 165.0 MHz maximum pixel clock
[ 60884.626] (--) NVIDIA(GPU-0): 
[ 60884.626] (--) NVIDIA(GPU-0): DFP-6: disconnected
[ 60884.626] (--) NVIDIA(GPU-0): DFP-6: Internal DisplayPort
[ 60884.626] (--) NVIDIA(GPU-0): DFP-6: 1440.0 MHz maximum pixel clock
[ 60884.626] (--) NVIDIA(GPU-0): 
[ 60884.626] (--) NVIDIA(GPU-0): DFP-7: disconnected
[ 60884.626] (--) NVIDIA(GPU-0): DFP-7: Internal TMDS
[ 60884.626] (--) NVIDIA(GPU-0): DFP-7: 165.0 MHz maximum pixel clock
[ 60884.626] (--) NVIDIA(GPU-0): 
[ 60884.648] (II) NVIDIA(0): Setting mode "DVI-D-0: nvidia-auto-select @1920x1080 +1920+0 {ViewPortIn=1920x1080, ViewPortOut=1920x1080+0+0}"
[ 60884.852] (II) NVIDIA(0): Setting mode "DVI-D-0: nvidia-auto-select @1920x1080 +0+0 {ViewPortIn=1920x1080, ViewPortOut=1920x1080+0+0}"
[ 60884.900] (II) NVIDIA(0): Setting mode "DVI-D-0: nvidia-auto-select @1920x1080 +0+0 {ViewPortIn=1920x1080, ViewPortOut=1920x1080+0+0}, HDMI-0: nvidia-auto-select @1920x1080 +1920+0 {ViewPortIn=1920x1080, ViewPortOut=1920x1080+0+0}"
[ 60885.230] (--) NVIDIA(GPU-0): Ancor Communications Inc ASUS VS239 (DFP-0): connected
[ 60885.230] (--) NVIDIA(GPU-0): Ancor Communications Inc ASUS VS239 (DFP-0): Internal TMDS
[ 60885.230] (--) NVIDIA(GPU-0): Ancor Communications Inc ASUS VS239 (DFP-0): 600.0 MHz maximum pixel clock
[ 60885.230] (--) NVIDIA(GPU-0): 
[ 60885.245] (--) NVIDIA(GPU-0): Ancor Communications Inc ASUS VS239 (DFP-1): connected
[ 60885.245] (--) NVIDIA(GPU-0): Ancor Communications Inc ASUS VS239 (DFP-1): Internal TMDS
[ 60885.245] (--) NVIDIA(GPU-0): Ancor Communications Inc ASUS VS239 (DFP-1): 165.0 MHz maximum pixel clock
[ 60885.245] (--) NVIDIA(GPU-0): 
[ 60885.245] (--) NVIDIA(GPU-0): DFP-2: disconnected
[ 60885.245] (--) NVIDIA(GPU-0): DFP-2: Internal DisplayPort
[ 60885.245] (--) NVIDIA(GPU-0): DFP-2: 1440.0 MHz maximum pixel clock
[ 60885.245] (--) NVIDIA(GPU-0): 
[ 60885.320] (--) NVIDIA(GPU-0): Ancor Communications Inc ASUS VS239 (DFP-3): connected
[ 60885.320] (--) NVIDIA(GPU-0): Ancor Communications Inc ASUS VS239 (DFP-3): Internal TMDS
[ 60885.320] (--) NVIDIA(GPU-0): Ancor Communications Inc ASUS VS239 (DFP-3): 600.0 MHz maximum pixel clock
[ 60885.320] (--) NVIDIA(GPU-0): 
[ 60885.320] (--) NVIDIA(GPU-0): DFP-4: disconnected
[ 60885.320] (--) NVIDIA(GPU-0): DFP-4: Internal DisplayPort
[ 60885.320] (--) NVIDIA(GPU-0): DFP-4: 1440.0 MHz maximum pixel clock
[ 60885.320] (--) NVIDIA(GPU-0): 
[ 60885.320] (--) NVIDIA(GPU-0): DFP-5: disconnected
[ 60885.320] (--) NVIDIA(GPU-0): DFP-5: Internal TMDS
[ 60885.320] (--) NVIDIA(GPU-0): DFP-5: 165.0 MHz maximum pixel clock
[ 60885.320] (--) NVIDIA(GPU-0): 
[ 60885.320] (--) NVIDIA(GPU-0): DFP-6: disconnected
[ 60885.320] (--) NVIDIA(GPU-0): DFP-6: Internal DisplayPort
[ 60885.321] (--) NVIDIA(GPU-0): DFP-6: 1440.0 MHz maximum pixel clock
[ 60885.321] (--) NVIDIA(GPU-0): 
[ 60885.321] (--) NVIDIA(GPU-0): DFP-7: disconnected
[ 60885.321] (--) NVIDIA(GPU-0): DFP-7: Internal TMDS
[ 60885.321] (--) NVIDIA(GPU-0): DFP-7: 165.0 MHz maximum pixel clock
[ 60885.321] (--) NVIDIA(GPU-0): 
[ 60885.385] (--) NVIDIA(GPU-0): Ancor Communications Inc ASUS VS239 (DFP-3): connected
[ 60885.385] (--) NVIDIA(GPU-0): Ancor Communications Inc ASUS VS239 (DFP-3): Internal TMDS
[ 60885.385] (--) NVIDIA(GPU-0): Ancor Communications Inc ASUS VS239 (DFP-3): 600.0 MHz maximum pixel clock
[ 60885.385] (--) NVIDIA(GPU-0): 
[ 60885.473] (II) NVIDIA(0): Setting mode "DVI-D-0: nvidia-auto-select @1920x1080 +1920+0 {ViewPortIn=1920x1080, ViewPortOut=1920x1080+0+0}, HDMI-0: nvidia-auto-select @1920x1080 +1920+0 {ViewPortIn=1920x1080, ViewPortOut=1920x1080+0+0}"
[ 60885.672] (II) NVIDIA(0): Setting mode "DVI-D-0: nvidia-auto-select @1920x1080 +1920+0 {ViewPortIn=1920x1080, ViewPortOut=1920x1080+0+0}, DP-1: nvidia-auto-select @1920x1080 +0+0 {ViewPortIn=1920x1080, ViewPortOut=1920x1080+0+0}"
[ 60885.926] (II) NVIDIA(0): Setting mode "DVI-D-0: nvidia-auto-select @1920x1080 +1920+0 {ViewPortIn=1920x1080, ViewPortOut=1920x1080+0+0}, DP-1: nvidia-auto-select @1920x1080 +0+0 {ViewPortIn=1920x1080, ViewPortOut=1920x1080+0+0}, HDMI-0: nvidia-auto-select @1920x1080 +3840+0 {ViewPortIn=1920x1080, ViewPortOut=1920x1080+0+0}"
[ 60891.079] (--) NVIDIA(GPU-0): Ancor Communications Inc ASUS VS239 (DFP-0): connected
[ 60891.079] (--) NVIDIA(GPU-0): Ancor Communications Inc ASUS VS239 (DFP-0): Internal TMDS
[ 60891.079] (--) NVIDIA(GPU-0): Ancor Communications Inc ASUS VS239 (DFP-0): 600.0 MHz maximum pixel clock
[ 60891.079] (--) NVIDIA(GPU-0): 
[ 60891.094] (--) NVIDIA(GPU-0): Ancor Communications Inc ASUS VS239 (DFP-1): connected
[ 60891.094] (--) NVIDIA(GPU-0): Ancor Communications Inc ASUS VS239 (DFP-1): Internal TMDS
[ 60891.094] (--) NVIDIA(GPU-0): Ancor Communications Inc ASUS VS239 (DFP-1): 165.0 MHz maximum pixel clock
[ 60891.094] (--) NVIDIA(GPU-0): 
[ 60891.094] (--) NVIDIA(GPU-0): DFP-2: disconnected
[ 60891.094] (--) NVIDIA(GPU-0): DFP-2: Internal DisplayPort
[ 60891.094] (--) NVIDIA(GPU-0): DFP-2: 1440.0 MHz maximum pixel clock
[ 60891.094] (--) NVIDIA(GPU-0): 
[ 60891.159] (--) NVIDIA(GPU-0): Ancor Communications Inc ASUS VS239 (DFP-3): connected
[ 60891.159] (--) NVIDIA(GPU-0): Ancor Communications Inc ASUS VS239 (DFP-3): Internal TMDS
[ 60891.159] (--) NVIDIA(GPU-0): Ancor Communications Inc ASUS VS239 (DFP-3): 600.0 MHz maximum pixel clock
[ 60891.159] (--) NVIDIA(GPU-0): 
[ 60891.159] (--) NVIDIA(GPU-0): DFP-4: disconnected
[ 60891.159] (--) NVIDIA(GPU-0): DFP-4: Internal DisplayPort
[ 60891.159] (--) NVIDIA(GPU-0): DFP-4: 1440.0 MHz maximum pixel clock
[ 60891.159] (--) NVIDIA(GPU-0): 
[ 60891.159] (--) NVIDIA(GPU-0): DFP-5: disconnected
[ 60891.159] (--) NVIDIA(GPU-0): DFP-5: Internal TMDS
[ 60891.159] (--) NVIDIA(GPU-0): DFP-5: 165.0 MHz maximum pixel clock
[ 60891.159] (--) NVIDIA(GPU-0): 
[ 60891.159] (--) NVIDIA(GPU-0): DFP-6: disconnected
[ 60891.159] (--) NVIDIA(GPU-0): DFP-6: Internal DisplayPort
[ 60891.159] (--) NVIDIA(GPU-0): DFP-6: 1440.0 MHz maximum pixel clock
[ 60891.159] (--) NVIDIA(GPU-0): 
[ 60891.160] (--) NVIDIA(GPU-0): DFP-7: disconnected
[ 60891.160] (--) NVIDIA(GPU-0): DFP-7: Internal TMDS
[ 60891.160] (--) NVIDIA(GPU-0): DFP-7: 165.0 MHz maximum pixel clock
[ 60891.160] (--) NVIDIA(GPU-0): 



```

---

### Post by duckyduckyducky on 2019-01-21
Bump.  Anyone have any ideas?

---

### Post by cam17 on 2019-02-08
I have the same problem with my Acer. If I perform a new install but do not update 18.04.1 LTS the system does not crash. I have heard on security now episode 700 "700 and counting!" that there is a security problem with systemd mallware issue.

I have updated my workstation today feb-8-2018 to see if it still occurs.

---

