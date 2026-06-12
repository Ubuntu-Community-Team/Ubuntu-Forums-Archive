---
title: "2nd monitor not detected after X restart"
date: 2010-01-25
forum: Hardware
---

### Post by zippaplick on 2010-01-25
Hi,

I've got dual monitors running off my docking station, nvidia card on my laptop.
If I set up twinview via "sudo nvidia-settings", save the new xorg.conf, and apply the settings, then both monitors work fine.

Problem is after restarting X the 2nd monitor isn't detected. If I run nvidia-settings, activate the 2nd monitor with twinview, and apply the settings it works.

This is not optimal. I'd really like to have both monitors be detected on startup and "just work".

Any ideas?

Here's what Xorg.0.log says:

(--) NVIDIA(0): Connected display device(s) on GeForce Go 7400 at PCI:1:0:0:                                                                                         
(--) NVIDIA(0):     DELL 2407WFP (CRT-0)                                                                                                                             
(--) NVIDIA(0):     Seiko (DFP-0)                                                                                                                                    
(--) NVIDIA(0):     DELL 2407WFP (DFP-1)                                                                                                                             
(--) NVIDIA(0): DELL 2407WFP (CRT-0): 400.0 MHz maximum pixel clock                                                                                                  
(--) NVIDIA(0): Seiko (DFP-0): 330.0 MHz maximum pixel clock                                                                                                         
(--) NVIDIA(0): Seiko (DFP-0): Internal Dual Link LVDS                                                                                                               
(--) NVIDIA(0): DELL 2407WFP (DFP-1): 165.0 MHz maximum pixel clock                                                                                                  
(--) NVIDIA(0): DELL 2407WFP (DFP-1): Internal Single Link TMDS                                                                                                      
(**) NVIDIA(0): TwinView enabled                                                                                                                                     
(II) NVIDIA(0): Display Devices found referenced in MetaMode: CRT-0, DFP-0,                                                                                          
(II) NVIDIA(0):     DFP-1                                                                                                                                            
(WW) NVIDIA(0): There are only 2 CRTCs available, trimming display device list                                                                                       
(WW) NVIDIA(0):     from "CRT-0, DFP-0, DFP-1" to "CRT-0, DFP-0".                                                                                                    
(II) NVIDIA(0): Assigned Display Devices: CRT-0, DFP-0                                                                                                               
(WW) NVIDIA(0): Invalid display device in Mode Description                                                                                                           
(WW) NVIDIA(0):     "DFP-1:nvidia-auto-select+1920+0"                                                                                                                
(WW) NVIDIA(0): Not using mode description "DFP-1:nvidia-auto-select+1920+0";                                                                                        
(WW) NVIDIA(0):     unable to map to display device                                                                                                                  
(II) NVIDIA(0): Validated modes:                                                                                                                                     
(II) NVIDIA(0):                                                                                                                                                      
(II) NVIDIA(0):     "CRT:nvidia-auto-select+0+0,DFP-0:NULL,DFP-1:nvidia-auto-select+1920+0"                                                                          
(II) NVIDIA(0): Virtual screen size determined to be 1920 x 1200            


Thanks for any help!

---

### Post by zippaplick on 2010-02-03
Fixed by adding this line to my xorg.conf's Screen section:


Option "ConnectedMonitor" "CRT, DFP-1"

---

