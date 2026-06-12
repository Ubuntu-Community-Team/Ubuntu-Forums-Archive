---
title: "usb_modeswitch is working only when I am running the command twice."
date: 2016-12-27
forum: Hardware
---

### Post by pankajcharpe on 2016-12-27
Hi,

       I am using libusb-1.0.21 version , usb_modeswitch-2.4.0 and kernel-3.10.14 ,when the first time I am running  usb_modeswitch command its is not switching and when I run the command for second time it is switching.I don't know why I have to run it twice to make it working,I want to do this only once.Below is the complete log ,Please help me to resolve this issue.

```
# usb 1-2: new high-speed USB device number 6 using xhci-hcd                      
usb 1-2: New USB device found, idVendor=12d1, idProduct=1446                      
usb 1-2: New USB device strings: Mfr=3, Product=2, SerialNumber=0                 
usb 1-2: Product: HUAWEI Mobile                                                   
usb 1-2: Manufacturer: HUAWEI Technology                                          
add_ep parameters, dev_speed 3, is_in 1, isTT 0, ep_type 2, maxp 512, interval 1,0
add_ep parameters, dev_speed 3, is_in 0, isTT 0, ep_type 2, maxp 512, interval 1,0
add_ep parameters, dev_speed 3, is_in 0, isTT 0, ep_type 2, maxp 512, interval 1,0
add_ep parameters, dev_speed 3, is_in 1, isTT 0, ep_type 2, maxp 512, interval 1,0
usb-storage 1-2:1.0: USB Mass Storage device detected                             
scsi16 : usb-storage 1-2:1.0                                                      
usb-storage 1-2:1.1: USB Mass Storage device detected                             
scsi17 : usb-storage 1-2:1.1                                                      
scsi 16:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2     
scsi 17:0:0:0: Direct-Access     HUAWEI   SD Storage       2.31 PQ: 0 ANSI: 2     
sd 17:0:0:0: [sda] Attached SCSI removable disk                                   
2                                                                                 
                                                                                 
#                                                                              
#                                                                                 
**# usb_modeswitch -c /etc_ro/usb/usb_modeswitch_HUAWEI-E169.conf **  
                
[timestamp] [threadID] facility level [function call] <message>                   
--------------------------------------------------------------------------------  
[ 0.000000] [000058a5] libusb: debug [libusb_init] created default context        
[ 0.000100] [000058a5] libusb: debug [libusb_init] libusb v1.0.21.11156           
[ 0.000380] [000058a5] libusb: debug [find_usbfs_path] found usbfs at /sys/bus/us2
[ 0.000460] [000058a5] libusb: debug [op_init] bulk continuation flag supported   
[ 0.000500] [000058a5] libusb: debug [op_init] zero length packet flag supported  
[ 0.000560] [000058a5] libusb: debug [op_init] sysfs can relate devices           
[ 0.000600] [000058a5] libusb: debug [op_init] sysfs has complete descriptors     
[ 0.001000] [000058a6] libusb: debug [linux_netlink_event_thread_main] netlink evg
                                                                                  
                                                                   
[ 0.001100] [000058a5] libusb: debug [linux_get_device_address] getting address f0
[ 0.001120] [000058a5] libusb: debug [linux_get_device_address] scan 1-2          
[ 0.001500] [000058a5] libusb: debug [linux_get_device_address] bus=1 dev=6       
[ 0.001540] [000058a5] libusb: debug [linux_enumerate_device] busnum 1 devaddr 6 2
[ 0.001580] [000058a5] libusb: debug [linux_enumerate_device] allocating new devi)
[ 0.001840] [000058a5] libusb: debug [linux_get_parent_info] parent_dev usb1 not w
                                                                                  
                                                                   
[ 0.001900] [000058a5] libusb: debug [linux_get_device_address] getting address f0
[ 0.001940] [000058a5] libusb: debug [linux_get_device_address] scan usb1         
[ 0.002120] [000058a5] libusb: debug [linux_get_device_address] bus=1 dev=1       
[ 0.002220] [000058a5] libusb: debug [linux_enumerate_device] busnum 1 devaddr 1 7
[ 0.002260] [000058a5] libusb: debug [linux_enumerate_device] allocating new devi)
[ 0.002460] [000058a5] libusb: debug [linux_get_parent_info] Dev 0x424278 (1-2) h2
                                                                                  
                                                                  
[ 0.002540] [000058a5] libusb: debug [linux_get_device_address] getting address f0
[ 0.002580] [000058a5] libusb: debug [linux_get_device_address] scan usb1         
[ 0.002760] [000058a5] libusb: debug [linux_get_device_address] bus=1 dev=1       
[ 0.002800] [000058a5] libusb: debug [linux_enumerate_device] busnum 1 devaddr 1 7
[ 0.002820] [000058a5] libusb: debug [linux_enumerate_device] session_id 257 alres
                                                                                  
                                                                  
[ 0.002880] [000058a5] libusb: debug [linux_get_device_address] getting address f0
[ 0.002920] [000058a5] libusb: debug [linux_get_device_address] scan usb2         
[ 0.003100] [000058a5] libusb: debug [linux_get_device_address] bus=2 dev=1       
[ 0.003140] [000058a5] libusb: debug [linux_enumerate_device] busnum 2 devaddr 1 3
[ 0.003180] [000058a5] libusb: debug [linux_enumerate_device] allocating new devi)
[ 0.003400] [000058a5] libusb: debug [usbi_add_pollfd] add fd 6 events 1          
[ 0.003480] [000058a5] libusb: debug [usbi_io_init] using timerfd for timeouts    
[ 0.003520] [000058a5] libusb: debug [usbi_add_pollfd] add fd 8 events 1          
Look for target devices ...                                                       
[ 0.003580] [000058a5] libusb: debug [libusb_get_device_list]                     
[ 0.003660] [000058a5] libusb: debug [libusb_get_device_descriptor]               
[ 0.003680] [000058a5] libusb: debug [libusb_get_device_descriptor]               
[ 0.003740] [000058a5] libusb: debug [libusb_get_device_descriptor]               
 No devices in target mode or class found                                         
Look for default devices ...                                                      
[ 0.003800] [000058a5] libusb: debug [libusb_get_device_list]                     
[ 0.003820] [000058a5] libusb: debug [libusb_get_device_descriptor]               
[ 0.003860] [000058a5] libusb: debug [libusb_get_device_descriptor]               
   product ID matched                                                             
[ 0.003880] [000058a5] libusb: debug [libusb_get_device_descriptor]               
 Found devices in default mode (1)                                                
Access device 006 on bus 001                                                      
[ 0.003980] [000058a5] libusb: debug [libusb_open] open 1.6                      
                                                                                  
                                                       
                                                               
[ 0.010740] [000058a5] libusb: debug [usbi_add_pollfd] add fd 9 events 4          
                                                                                  
                                                        
Get the current device configuration ...                                          
Current configuration number is 1                                                 
[ 0.672240] [000058a5] libusb: debug [libusb_get_device_descriptor]               
Use interface number 0                                                            
Use endpoints 0x01 (out) and 0x81 (in)                                            
                                                                                  
USB description data (for identification)                                         
[ 0.672440] [000058a5] libusb: debug [libusb_get_device_descriptor]               
[ 0.672480] [000058a5] libusb: debug [libusb_alloc_transfer] transfer 0x427f70    
[ 0.672560] [000058a5] libusb: debug [libusb_submit_transfer] transfer 0x427f70   
[ 0.672580] [000058a5] libusb: debug [add_to_flying_list] arm timerfd for timeout)
[ 0.672720] [000058a5] libusb: debug [libusb_handle_events_timeout_completed] doig
[ 0.672760] [000058a5] libusb: debug [handle_events] poll fds modified, reallocatg
[ 0.672800] [000058a5] libusb: debug [handle_events] poll() 3 fds with timeout ins
[ 0.673200] [000058a5] libusb: debug [handle_events] poll() returned 1            
[ 0.673260] [000058a5] libusb: debug [reap_for_handle] urb type=2 status=0 transf4
[ 0.673300] [000058a5] libusb: debug [handle_control_completion] handling complet0
[ 0.673340] [000058a5] libusb: debug [disarm_timerfd]                             
[ 0.673360] [000058a5] libusb: debug [usbi_handle_transfer_completion] transfer 00
[ 0.673400] [000058a5] libusb: debug [sync_transfer_cb] actual_length=4           
[ 0.673440] [000058a5] libusb: debug [libusb_free_transfer] transfer 0x427f70     
[ 0.673480] [000058a5] libusb: debug [libusb_alloc_transfer] transfer 0x427f70    
[ 0.673520] [000058a5] libusb: debug [libusb_submit_transfer] transfer 0x427f70   
[ 0.673540] [000058a5] libusb: debug [add_to_flying_list] arm timerfd for timeout)
[ 0.673600] [000058a5] libusb: debug [libusb_handle_events_timeout_completed] doig
[ 0.673640] [000058a5] libusb: debug [handle_events] poll() 3 fds with timeout ins
[ 0.673920] [000058a5] libusb: debug [handle_events] poll() returned 1            
[ 0.673960] [000058a5] libusb: debug [reap_for_handle] urb type=2 status=0 transf6
[ 0.674000] [000058a5] libusb: debug [handle_control_completion] handling complet0
[ 0.674020] [000058a5] libusb: debug [disarm_timerfd]                             
[ 0.674060] [000058a5] libusb: debug [usbi_handle_transfer_completion] transfer 00
[ 0.674080] [000058a5] libusb: debug [sync_transfer_cb] actual_length=36          
[ 0.674140] [000058a5] libusb: debug [libusb_free_transfer] transfer 0x427f70     
[ 0.674200] [000058a5] libusb: debug [libusb_alloc_transfer] transfer 0x427f70    
[ 0.674240] [000058a5] libusb: debug [libusb_submit_transfer] transfer 0x427f70   
[ 0.674260] [000058a5] libusb: debug [add_to_flying_list] arm timerfd for timeout)
[ 0.674320] [000058a5] libusb: debug [libusb_handle_events_timeout_completed] doig
[ 0.674360] [000058a5] libusb: debug [handle_events] poll() 3 fds with timeout ins
[ 0.674620] [000058a5] libusb: debug [handle_events] poll() returned 1            
[ 0.674660] [000058a5] libusb: debug [reap_for_handle] urb type=2 status=0 transf4
[ 0.674700] [000058a5] libusb: debug [handle_control_completion] handling complet0
[ 0.674720] [000058a5] libusb: debug [disarm_timerfd]                             
[ 0.674760] [000058a5] libusb: debug [usbi_handle_transfer_completion] transfer 00
[ 0.674780] [000058a5] libusb: debug [sync_transfer_cb] actual_length=4           
[ 0.674820] [000058a5] libusb: debug [libusb_free_transfer] transfer 0x427f70     
[ 0.674860] [000058a5] libusb: debug [libusb_alloc_transfer] transfer 0x427f70    
[ 0.674880] [000058a5] libusb: debug [libusb_submit_transfer] transfer 0x427f70   
[ 0.674920] [000058a5] libusb: debug [add_to_flying_list] arm timerfd for timeout)
[ 1.338200] [000058a5] libusb: debug [libusb_handle_events_timeout_completed] doig
[ 1.338280] [000058a5] libusb: debug [handle_events] poll() 3 fds with timeout ins
[ 1.338620] [000058a5] libusb: debug [handle_events] poll() returned 1            
[ 1.338680] [000058a5] libusb: debug [reap_for_handle] urb type=2 status=0 transf8
[ 1.338700] [000058a5] libusb: debug [handle_control_completion] handling complet0
[ 1.338740] [000058a5] libusb: debug [disarm_timerfd]                             
[ 1.338780] [000058a5] libusb: debug [usbi_handle_transfer_completion] transfer 00
[ 1.338800] [000058a5] libusb: debug [sync_transfer_cb] actual_length=28          
[ 1.338840] [000058a5] libusb: debug [libusb_free_transfer] transfer 0x427f70     
-------------------------                                                         
Manufacturer: HUAWEI Technology                                                   
     Product: HUAWEI Mobile                                                       
  Serial No.: not provided                                                        
-------------------------                                                         
Looking for active driver ...                                                     
[ 1.338980] [000058a5] libusb: debug [libusb_kernel_driver_active] interface 0    
[ 1.339020] [000058a5] libusb: debug [libusb_detach_kernel_driver] interface 0    
 OK, driver detached                                                              
Set up interface 0                                                                
[ 1.345240] [000058a5] libusb: debug [libusb_claim_interface] interface 0         
[ 1.345400] [000058a5] libusb: debug [libusb_clear_halt] endpoint 1               
Use endpoint 0x01 for message sending ...                                         
Trying to send message 1 to endpoint 0x01 ...                                     
[ 1.345960] [000058a5] libusb: debug [libusb_alloc_transfer] transfer 0x427f70    
[ 1.346020] [000058a5] libusb: debug [libusb_submit_transfer] transfer 0x427f70   
[ 1.346060] [000058a5] libusb: debug [add_to_flying_list] arm timerfd for timeout)
[ 1.346140] [000058a5] libusb: debug [submit_bulk_transfer] need 1 urbs for new t1
[ 1.346360] [000058a5] libusb: debug [libusb_handle_events_timeout_completed] doig
[ 1.346440] [000058a5] libusb: debug [handle_events] poll() 3 fds with timeout ins
[ 1.346500] [000058a5] libusb: debug [handle_events] poll() returned 1            
[ 1.346560] [000058a5] libusb: debug [reap_for_handle] urb type=3 status=0 transf1
[ 1.346620] [000058a5] libusb: debug [handle_bulk_completion] handling completion1
[ 1.346680] [000058a5] libusb: debug [handle_bulk_completion] last URB in transfe!
[ 1.346720] [000058a5] libusb: debug [disarm_timerfd]                             
[ 1.346780] [000058a5] libusb: debug [usbi_handle_transfer_completion] transfer 00
[ 1.346840] [000058a5] libusb: debug [sync_transfer_cb] actual_length=31          
[ 1.346900] [000058a5] libusb: debug [libusb_free_transfer] transfer 0x427f70     
 OK, message successfully sent                                                    
Read the response to message 1 (CSW) ...                                          
                                                                                  
                                                                      
[ 1.347060] [000058a5] libusb: debug [libusb_alloc_transfer] transfer 0x427f70    
[ 1.347100] [000058a5] libusb: debug [libusb_submit_transfer] transfer 0x427f70   
[ 1.347140] [000058a5] libusb: debug [add_to_flying_list] arm timerfd for timeout)
[ 1.347200] [000058a5] libusb: debug [submit_bulk_transfer] need 1 urbs for new t3
[ 1.347340] [000058a5] libusb: debug [libusb_handle_events_timeout_completed] doig
[ 1.347400] [000058a5] libusb: debug [handle_events] poll() 3 fds with timeout ins
[ 4.350140] [000058a5] libusb: debug [handle_events] poll() returned 1            
[ 4.350240] [000058a5] libusb: debug [handle_events] timerfd triggered            
[ 4.350300] [000058a5] libusb: debug [libusb_cancel_transfer] transfer 0x427f70   
[ 4.350420] [000058a5] libusb: debug [disarm_timerfd]                             
[ 4.350460] [000058a5] libusb: debug [handle_events] poll() 3 fds with timeout ins
[ 4.350500] [000058a5] libusb: debug [handle_events] poll() returned 1            
[ 4.350540] [000058a5] libusb: debug [reap_for_handle] urb type=3 status=-2 trans0
[ 4.350560] [000058a5] libusb: debug [handle_bulk_completion] handling completion1
[ 4.350600] [000058a5] libusb: debug [handle_bulk_completion] abnormal reap: urb 2
[ 4.350620] [000058a5] libusb: debug [handle_bulk_completion] abnormal reap: lastg
[ 4.350660] [000058a5] libusb: debug [usbi_handle_transfer_cancellation] detectedn
[ 4.350680] [000058a5] libusb: debug [disarm_timerfd]                             
[ 4.350720] [000058a5] libusb: debug [usbi_handle_transfer_completion] transfer 00
[ 4.350740] [000058a5] libusb: debug [sync_transfer_cb] actual_length=0           
[ 4.350800] [000058a5] libusb: debug [libusb_free_transfer] transfer 0x427f70     
[B] [COLOR=#FF0000]Response reading failed (error -7)                                          
   
                                                            
                                                                                  
 Device is gone, skip any further commands [/COLOR] [/B]                                      
[ 4.350880] [000058a5] libusb: debug [libusb_close]                               
[ 4.350940] [000058a5] libusb: debug [usbi_remove_pollfd] remove fd 9             
                                                                                  
Check for mode switch (max. 5 times, once per second) ...                         
[ 4.629680] [000058a6] libusb: debug [linux_netlink_parse] unknown device action e
[ 5.354180] [000058a5] libusb: debug [libusb_exit]                                
[ 5.354280] [000058a5] libusb: debug [libusb_exit] destroying default context     
[ 5.354320] [000058a5] libusb: debug [libusb_handle_events_timeout_completed] doig
[ 5.354340] [000058a5] libusb: debug [handle_events] poll fds modified, reallocatg
[ 5.354400] [000058a5] libusb: debug [handle_events] poll() 2 fds with timeout ins
[ 5.354440] [000058a5] libusb: debug [handle_events] poll() returned 0            
[ 5.354480] [000058a5] libusb: debug [usbi_remove_pollfd] remove fd 6             
[ 5.354560] [000058a5] libusb: debug [usbi_remove_pollfd] remove fd 8             
[ 5.354680] [000058a6] libusb: debug [linux_netlink_event_thread_main] netlink evg
#                                                                                 
#                                                                                 
#                                                                                 
#                                                                                 
#                                                                                 
**# usb_modeswitch -c /etc_ro/usb/usb_modeswitch_HUAWEI-E169.conf  ** 
                
[timestamp] [threadID] facility level [function call] <message>                   
--------------------------------------------------------------------------------  
[ 0.000000] [00005916] libusb: debug [libusb_init] created default context        
[ 0.000100] [00005916] libusb: debug [libusb_init] libusb v1.0.21.11156           
[ 0.000360] [00005916] libusb: debug [find_usbfs_path] found usbfs at /sys/bus/us2
[ 0.000440] [00005916] libusb: debug [op_init] bulk continuation flag supported   
[ 0.000480] [00005916] libusb: debug [op_init] zero length packet flag supported  
[ 0.000560] [00005916] libusb: debug [op_init] sysfs can relate devices           
[ 0.000580] [00005916] libusb: debug [op_init] sysfs has complete descriptors     
[ 0.000880] [00005917] libusb: debug [linux_netlink_event_thread_main] netlink evg
                                                                                  
                                                                     
[ 0.000960] [00005916] libusb: debug [linux_get_device_address] getting address f0
[ 0.001000] [00005916] libusb: debug [linux_get_device_address] scan 1-2          
[ 0.001260] [00005916] libusb: debug [linux_get_device_address] bus=1 dev=6       
[ 0.001300] [00005916] libusb: debug [linux_enumerate_device] busnum 1 devaddr 6 2
[ 0.001320] [00005916] libusb: debug [linux_enumerate_device] allocating new devi)
[ 0.001560] [00005916] libusb: debug [linux_get_parent_info] parent_dev usb1 not w
                                                                                  
                                                                 
[ 0.001620] [00005916] libusb: debug [linux_get_device_address] getting address f0
[ 0.001660] [00005916] libusb: debug [linux_get_device_address] scan usb1         
[ 0.002020] [00005916] libusb: debug [linux_get_device_address] bus=1 dev=1       
[ 0.002080] [00005916] libusb: debug [linux_enumerate_device] busnum 1 devaddr 1 7
[ 0.002160] [00005916] libusb: debug [linux_enumerate_device] allocating new devi)
[ 0.002380] [00005916] libusb: debug [linux_get_parent_info] Dev 0x424278 (1-2) h2
                                                                                  
                                                                   
[ 0.002460] [00005916] libusb: debug [linux_get_device_address] getting address f0
[ 0.002560] [00005916] libusb: debug [linux_get_device_address] scan usb1         
[ 0.002760] [00005916] libusb: debug [linux_get_device_address] bus=1 dev=1       
[ 0.002800] [00005916] libusb: debug [linux_enumerate_device] busnum 1 devaddr 1 7
[ 0.002880] [00005916] libusb: debug [linux_enumerate_device] session_id 257 alres
                                                                    
[ 0.002940] [00005916] libusb: debug [linux_get_device_address] getting address f0
[ 0.002980] [00005916] libusb: debug [linux_get_device_address] scan usb2         
[ 0.003160] [00005916] libusb: debug [linux_get_device_address] bus=2 dev=1       
[ 0.003200] [00005916] libusb: debug [linux_enumerate_device] busnum 2 devaddr 1 3
[ 0.003240] [00005916] libusb: debug [linux_enumerate_device] allocating new devi)
[ 0.003500] [00005916] libusb: debug [usbi_add_pollfd] add fd 6 events 1          
[ 0.003560] [00005916] libusb: debug [usbi_io_init] using timerfd for timeouts    
[ 0.003600] [00005916] libusb: debug [usbi_add_pollfd] add fd 8 events 1          
Look for target devices ...                                                       
[ 0.003660] [00005916] libusb: debug [libusb_get_device_list]                     
[ 0.003740] [00005916] libusb: debug [libusb_get_device_descriptor]               
[ 0.003760] [00005916] libusb: debug [libusb_get_device_descriptor]               
[ 0.003820] [00005916] libusb: debug [libusb_get_device_descriptor]               
 No devices in target mode or class found                                         
Look for default devices ...                                                      
[ 0.003860] [00005916] libusb: debug [libusb_get_device_list]                     
[ 0.003900] [00005916] libusb: debug [libusb_get_device_descriptor]               
[ 0.003920] [00005916] libusb: debug [libusb_get_device_descriptor]               
   product ID matched                                                             
[ 0.003960] [00005916] libusb: debug [libusb_get_device_descriptor]               
 Found devices in default mode (1)                                                
Access device 006 on bus 001                                                      
[ 0.004020] [00005916] libusb: debug [libusb_open] open 1.6                       
                                                                 
[ 0.010760] [00005916] libusb: debug [usbi_add_pollfd] add fd 9 events 4          
                                                                                  
                                                        
Get the current device configuration ...                                          
Current configuration number is 1                                                 
[ 0.672200] [00005916] libusb: debug [libusb_get_device_descriptor]               
Use interface number 0                                                            
Use endpoints 0x01 (out) and 0x81 (in)                                            
                                                                                  
USB description data (for identification)                                         
[ 0.672380] [00005916] libusb: debug [libusb_get_device_descriptor]               
[ 0.672420] [00005916] libusb: debug [libusb_alloc_transfer] transfer 0x427f70    
[ 0.672500] [00005916] libusb: debug [libusb_submit_transfer] transfer 0x427f70   
[ 0.672540] [00005916] libusb: debug [add_to_flying_list] arm timerfd for timeout)
[ 0.672640] [00005916] libusb: debug [libusb_handle_events_timeout_completed] doig
[ 0.672700] [00005916] libusb: debug [handle_events] poll fds modified, reallocatg
[ 0.672740] [00005916] libusb: debug [handle_events] poll() 3 fds with timeout ins
[ 0.673040] [00005916] libusb: debug [handle_events] poll() returned 1            
[ 0.673120] [00005916] libusb: debug [reap_for_handle] urb type=2 status=0 transf4
[ 0.673140] [00005916] libusb: debug [handle_control_completion] handling complet0
[ 0.673180] [00005916] libusb: debug [disarm_timerfd]                             
[ 0.673200] [00005916] libusb: debug [usbi_handle_transfer_completion] transfer 00
[ 0.673240] [00005916] libusb: debug [sync_transfer_cb] actual_length=4           
[ 0.673280] [00005916] libusb: debug [libusb_free_transfer] transfer 0x427f70     
[ 0.673320] [00005916] libusb: debug [libusb_alloc_transfer] transfer 0x427f70    
[ 0.673360] [00005916] libu# usb_modeswitch -c /etc_ro/usb/usb_modeswitch_HUAWEI-E169.conf sb: debug [libusb_submit_transfer] transfer 0x427f70   
[ 0.673380] [00005916] libusb: debug [add_to_flying_list] arm timerfd for timeout)
[ 0.673440] [00005916] libusb: debug [libusb_handle_events_timeout_completed] doig
[ 0.673480] [00005916] libusb: debug [handle_events] poll() 3 fds with timeout ins
[ 0.673780] [00005916] libusb: debug [handle_events] poll() returned 1            
[ 0.673820] [00005916] libusb: debug [reap_for_handle] urb type=2 status=0 transf6
[ 0.673840] [00005916] libusb: debug [handle_control_completion] handling complet0
[ 0.673880] [00005916] libusb: debug [disarm_timerfd]                             
[ 0.673940] [00005916] libusb: debug [usbi_handle_transfer_completion] transfer 00
[ 0.673980] [00005916] libusb: debug [sync_transfer_cb] actual_length=36          
[ 0.674020] [00005916] libusb: debug [libusb_free_transfer] transfer 0x427f70     
[ 0.674060] [00005916] libusb: debug [libusb_alloc_transfer] transfer 0x427f70    
[ 0.674100] [00005916] libusb: debug [libusb_submit_transfer] transfer 0x427f70   
[ 0.674120] [00005916] libusb: debug [add_to_flying_list] arm timerfd for timeout)
[ 0.674180] [00005916] libusb: debug [libusb_handle_events_timeout_completed] doig
[ 0.674220] [00005916] libusb: debug [handle_events] poll() 3 fds with timeout ins
[ 0.674480] [00005916] libusb: debug [handle_events] poll() returned 1            
[ 0.674520] [00005916] libusb: debug [reap_for_handle] urb type=2 status=0 transf4
[ 0.674560] [00005916] libusb: debug [handle_control_completion] handling complet0
[ 0.674580] [00005916] libusb: debug [disarm_timerfd]                             
[ 0.674620] [00005916] libusb: debug [usbi_handle_transfer_completion] transfer 00
[ 0.674640] [00005916] libusb: debug [sync_transfer_cb] actual_length=4           
[ 0.674680] [00005916] libusb: debug [libusb_free_transfer] transfer 0x427f70     
[ 0.674usb 1-2: USB disconnect, device number 6                                   
720] [00005916] libusb: debug [libusb_alloc_transfer] transfer 0x427f70           
[ 0.674740] [00005916] libusb: debug [libusb_submit_transfer] transfer 0x427f70   
[ 0.674780] [00005916] libusb: debug [add_to_flying_list] arm timerfd for timeout)
[ 1.338180] [00005916] libusb: debug [libusb_handle_events_timeout_completed] doig
[ 1.338260] [00005916] libusb: debug [handle_events] poll() 3 fds with timeout ins
[ 1.338620] [00005916] libusb: debug [handle_events] poll() returned 1            
[ 1.338660] [00005916] libusb: debug [reap_for_handle] urb type=2 status=0 transf8
[ 1.338700] [00005916] libusb: debug [handle_control_completion] handling complet0
[ 1.338740] [00005916] libusb: debug [disarm_timerfd]                             
[ 1.338760] [00005916] libusb: debug [usbi_handle_transfer_completion] transfer 00
[ 1.338800] [00005916] libusb: debug [sync_transfer_cb] actual_length=28          
[ 1.338840] [00005916] libusb: debug [libusb_free_transfer] transfer 0x427f70     
-------------------------                                                         
Manufacturer: HUAWEI Technology                                                   
     Product: HUAWEI Mobile                                                       
  Serial No.: not provided                                                        
-------------------------                                                         
Looking for active driver ...                                                     
[ 1.338980] [00005916] libusb: debug [libusb_kernel_driver_active] interface 0    
 No active driver found. Detached before or never attached                        
Set up interface 0                                                                
[ 1.339040] [00005916] libusb: debug [libusb_claim_interface] interface 0         
[ 1.339140] [00005916] libusb: debug [libusb_clear_halt] endpoint 1               
Use endpoint 0x01 for message sending ...                                         
Trying to send message 1 to endpoint 0x01 ...                                     
[ 1.339700] [00005916] libusb: debug [libusb_alloc_transfer] transfer 0x427f70    
[ 1.339720] [00005916] libusb: debug [libusb_submit_transfer] transfer 0x427f70   
[ 1.339760] [00005916] libusb: debug [add_to_flying_list] arm timerfd for timeout)
[ 1.339800] [00005916] libusb: debug [submit_bulk_transfer] need 1 urbs for new t1
[ 1.339880] [00005916] libusb: debug [libusb_handle_events_timeout_completed] doig
[ 1.339920] [00005916] libusb: debug [handle_events] poll() 3 fds with timeout ins
[ 1.339960] [00005916] libusb: debug [handle_events] poll() returned 1            
[ 1.340060] [00005916] libusb: debug [reap_for_handle] urb type=3 status=0 transf1
[ 1.340100] [00005916] libusb: debug [handle_bulk_completion] handling completion1
[ 1.340120] [00005916] libusb: debug [handle_bulk_completion] last URB in transfe!
[ 1.340160] [00005916] libusb: debug [disarm_timerfd]                             
[ 1.340240] [00005916] libusb: debug [usbi_handle_transfer_completion] transfer 00
[ 1.348320] [00005916] libusb: debug [sync_transfer_cb] actual_length=31          
[ 1.363300] [00005916] libusb: debug [libusb_free_transfer] transfer 0x427f70     
 OK, message successfully sent                                                    
[ 1.363280] [00005917] libusb: debug [linux_netlink_read_message] netlink hotplugs
Read the response to message 1 (CSW) ...                                          
                                                                                  
                                                                 
[ 1.363580] [00005916] libusb: debug [libusb_alloc_transfer] transfer 0x427f70    
[ 1.363620] [00005916] libusb: debug [libusb_submit_transfer] transfer 0x427f70   
[ 1.363680] [00005916] libusb: debug [add_to_flying_list] arm timerfd for timeout)
[ 1.363760] [00005916] libusb: debug [submit_bulk_transfer] need 1 urbs for new t3
[ 1.363840] [00005916] libusb: debug [submit_bulk_transfer] first URB failed, easy
[ 1.363880] [00005916] libusb: debug [disarm_timerfd]                             
[ 1.363940] [00005916] libusb: debug [libusb_free_transfer] transfer 0x427f70     
[COLOR=#00FF00][B][COLOR=#274E13] Device seems to have vanished after reading. Good.                               
                                                                 
                                                                                  
 Device is gone, skip any further commands[/COLOR][/B]  [/COLOR]                                      
[ 1.364080] [00005916] libusb: debug [libusb_close]                               
[ 1.364120] [00005916] libusb: debug [usbi_remove_pollfd] remove fd 9             
                                                                                  
Check for mode switch (max. 5 times, once per second) ...                         
4                                                                                 
[ 2.365960] [00005916] libusb: debug [libusb_exit]                                
[ 2.366060] [00005916] libusb: debug [libusb_exit] destroying default context     
[ 2.366100] [00005916] libusb: debug [libusb_handle_events_timeout_completed] doig
[ 2.366140] [00005916] libusb: debug [handle_events] poll fds modified, reallocatg
[ 2.366160] [00005916] libusb: debug [handle_events] poll() 2 fds with timeout ins
[ 2.366200] [00005916] libusb: debug [handle_events] poll() returned 1            
[ 2.366220] [00005916] libusb: debug [handle_events] caught a fish on the event pe
[ 2.366260] [00005916] libusb: debug [handle_events] hotplug message received     
[ 2.366300] [00005916] libusb: debug [handle_events] poll() 2 fds with timeout ins
[ 2.366340] [00005916] libusb: debug [handle_events] poll() returned 0            
[ 2.366380] [00005916] libusb: debug [usbi_remove_pollfd] remove fd 6             
[ 2.366460] [00005916] libusb: debug [usbi_remove_pollfd] remove fd 8             
[ 2.366600] [00005917] libusb: debug [linux_netlink_event_thread_main] netlink evg
# usb 1-2: new high-speed USB device number 7 using xhci-hcd                      
usb 1-2: New USB device found, idVendor=12d1, idProduct=1417                      
usb 1-2: New USB device strings: Mfr=3, Product=2, SerialNumber=0                 
usb 1-2: Product: HUAWEI Mobile                                                   
usb 1-2: Manufacturer: HUAWEI Technology                                          
add_ep parameters, dev_speed 3, is_in 1, isTT 0, ep_type 3, maxp 64, interval 16,0
add_ep parameters, dev_speed 3, is_in 1, isTT 0, ep_type 2, maxp 512, interval 320
add_ep parameters, dev_speed 3, is_in 0, isTT 0, ep_type 2, maxp 512, interval 320
add_ep parameters, dev_speed 3, is_in 1, isTT 0, ep_type 3, maxp 64, interval 16,0
add_ep parameters, dev_speed 3, is_in 1, isTT 0, ep_type 2, maxp 512, interval 320
add_ep parameters, dev_speed 3, is_in 0, isTT 0, ep_type 2, maxp 512, interval 320
add_ep parameters, dev_speed 3, is_in 1, isTT 0, ep_type 2, maxp 512, interval 320
add_ep parameters, dev_speed 3, is_in 0, isTT 0, ep_type 2, maxp 512, interval 320
add_ep parameters, dev_speed 3, is_in 1, isTT 0, ep_type 2, maxp 512, interval 320
add_ep parameters, dev_speed 3, is_in 0, isTT 0, ep_type 2, maxp 512, interval 320
add_ep parameters, dev_speed 3, is_in 0, isTT 0, ep_type 2, maxp 512, interval 1,0
add_ep parameters, dev_speed 3, is_in 1, isTT 0, ep_type 2, maxp 512, interval 1,0
add_ep parameters, dev_speed 3, is_in 0, isTT 0, ep_type 2, maxp 512, interval 1,0
add_ep parameters, dev_speed 3, is_in 1, isTT 0, ep_type 2, maxp 512, interval 1,0
usb-storage 1-2:1.0: USB Mass Storage device detected                             
option 1-2:1.0: GSM modem (1-port) converter detected                             
usb 1-2: GSM modem (1-port) converter now attached to ttyUSB0                     
usb-storage 1-2:1.1: USB Mass Storage device detected                             
option 1-2:1.1: GSM modem (1-port) converter detected                             
usb 1-2: GSM modem (1-port) converter now attached to ttyUSB1                     
usb-storage 1-2:1.2: USB Mass Storage device detected                             
option 1-2:1.2: GSM modem (1-port) converter detected                             
4                                                                                 
usb 1-2: GSM modem (1-port) converter now attached to ttyUSB2                     
0                                                                                 
usb-storage 1-2:1.3: USB Mass Storage device detected                             
option 1-2:1.3: GSM modem (1-port) converter detected                             
usb 1-2: GSM modem (1-port) converter now attached to ttyUSB3                     
usb-storage 1-2:1.4: USB Mass Storage device detected                             
option 1-2:1.4: GSM modem (1-port) converter detected                             
usb 1-2: GSM modem (1-port) converter now attached to ttyUSB4                     
usb-storage 1-2:1.5: USB Mass Storage device detected                             
scsi23 : usb-storage 1-2:1.5                                                      
scsi 23:0:0:0: Direct-Access     HUAWEI   SD Storage       2.31 PQ: 0 ANSI: 2     
sd 23:0:0:0: [sda] Attached SCSI removable disk
```

---

