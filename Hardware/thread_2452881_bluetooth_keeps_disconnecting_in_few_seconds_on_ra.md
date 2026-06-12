---
title: "bluetooth keeps disconnecting in few seconds on raspberry pi 4 running ubuntu desktop"
date: 2020-10-29
forum: Hardware
---

### Post by jordana2 on 2020-10-29
Can not get any bluetooth device connected on raspberry pi 4 running ubuntu desktop.
This is what bluetoothctl shows:
```


[bluetooth]# remove 20:20:01:1E:56:FF
[DEL] Device 20:20:01:1E:56:FF Bluetooth 3.0 Keyboard
Device has been removed

[NEW] Device 20:20:01:1E:56:FF Bluetooth 3.0 Keyboard

[bluetooth]# info 20:20:01:1E:56:FF
Device 20:20:01:1E:56:FF (public)
    Name: Bluetooth 3.0 Keyboard
    Alias: Bluetooth 3.0 Keyboard
    Class: 0x00002540
    Icon: input-keyboard
    Paired: no
    Trusted: no
    Blocked: no
    Connected: no
    LegacyPairing: yes
    RSSI: -43

[bluetooth]# pair 20:20:01:1E:56:FF
Attempting to pair with 20:20:01:1E:56:FF
[CHG] Device 20:20:01:1E:56:FF Connected: yes
[CHG] Device 20:20:01:1E:56:FF Connected: no

[bluetooth]# pair 20:20:01:1E:56:FF
Attempting to pair with 20:20:01:1E:56:FF
Failed to pair: org.bluez.Error.AlreadyExists


```

This is what btmon shows:

```


> HCI Event: Inquiry Result.. (0x22) plen 15  #590 [hci0] 165.880411  
        Num responses: 1           
        Address: 20:20:01:1E:56:FF (OUI 20-20-01)                     
        Page scan repetition mode: R1 (0x01)                          
        Page period mode: P0 (0x00)                                   
        Class: 0x002540            
          Major class: Peripheral (mouse, joystick, keyboards)        
          Minor class: 0x10        
          Limited Discoverable Mode                                   
        Clock offset: 0x1ad2       
        RSSI: -43 dBm (0xd5)       
@ MGMT Event: Device... (0x0012) plen 19  {0x0001} [hci0] 165.880508  
        BR/EDR Address: 20:20:01:1E:56:FF (OUI 20-20-01)              
        RSSI: -43 dBm (0xd5)       
        Flags: 0x00000003          
          Confirm Name             
          Legacy Pairing           
        Data length: 5             
        Class: 0x002540            
          Major class: Peripheral (mouse, joystick, keyboards)        
          Minor class: 0x10        
          Limited Discoverable Mode                                   
@ MGMT Command: Add De.. (0x0033) plen 8  {0x0001} [hci0] 166.157409  
        BR/EDR Address: 20:20:01:1E:56:FF (OUI 20-20-01)              
        Action: Allow incoming connection (0x01)                      
@ MGMT Event: Command.. (0x0001) plen 10  {0x0001} [hci0] 166.157524  
      Add Device (0x0033) plen 7   
        Status: Success (0x00)     
        BR/EDR Address: 20:20:01:1E:56:FF (OUI 20-20-01)              
@ MGMT Command: Stop D.. (0x0024) plen 1  {0x0001} [hci0] 166.158093  
        Address type: 0x07         
          BR/EDR                   
          LE Public                
          LE Random                
< HCI Command: Inquir.. (0x01|0x0002) plen 0  #591 [hci0] 166.158206  
> HCI Event: Command Complete (0x0e) plen 4   #592 [hci0] 166.160062  
      Inquiry Cancel (0x01|0x0002) ncmd 1                                                                                         [189/1847]
        Status: Success (0x00)     
@ MGMT Event: Discover.. (0x0013) plen 2  {0x0001} [hci0] 166.160205  
        Address type: 0x07         
          BR/EDR                   
          LE Public                
          LE Random                
        Discovery: Disabled (0x00)                                    
@ MGMT Event: Command... (0x0001) plen 4  {0x0001} [hci0] 166.160338  
      Stop Discovery (0x0024) plen 1                                  
        Status: Success (0x00)     
        Address type: 0x07         
          BR/EDR                   
          LE Public                
          LE Random                
@ MGMT Command: Pair D.. (0x0019) plen 8  {0x0001} [hci0] 166.161886  
        BR/EDR Address: 20:20:01:1E:56:FF (OUI 20-20-01)              
        Capability: KeyboardDisplay (0x04)                            
< HCI Command: Creat.. (0x01|0x0005) plen 13  #593 [hci0] 166.162006  
        Address: 20:20:01:1E:56:FF (OUI 20-20-01)                     
        Packet type: 0xcc18        
          DM1 may be used          
          DH1 may be used          
          DM3 may be used          
          DH3 may be used          
          DM5 may be used          
          DH5 may be used          
        Page scan repetition mode: R2 (0x02)                          
        Page scan mode: Mandatory (0x00)                              
        Clock offset: 0x0000       
        Role switch: Allow slave (0x01)                               
> HCI Event: Command Status (0x0f) plen 4     #594 [hci0] 166.162611  
      Create Connection (0x01|0x0005) ncmd 1                          
        Status: Success (0x00)     
> HCI Event: Connect Complete (0x03) plen 11  #595 [hci0] 167.179555  
        Status: Success (0x00)     
        Handle: 12                 
        Address: 20:20:01:1E:56:FF (OUI 20-20-01)                     
        Link type: ACL (0x01)      
        Encryption: Disabled (0x00)                                                                                               [150/1847]
< HCI Command: Read R.. (0x01|0x001b) plen 2  #596 [hci0] 167.179914  
        Handle: 12                 
> HCI Event: Command Status (0x0f) plen 4     #597 [hci0] 167.180760  
      Read Remote Supported Features (0x01|0x001b) ncmd 1             
        Status: Success (0x00)     
> HCI Event: Read Remote Su.. (0x0b) plen 11  #598 [hci0] 167.180863  
        Status: Success (0x00)     
        Handle: 12                 
        Features: 0xbf 0x06 0x86 0x78 0x18 0x1e 0x59 0x87             
          3 slot packets           
          5 slot packets           
          Encryption               
          Slot offset              
          Timing accuracy          
          Role switch              
          Sniff mode               
          Power control requests   
          Channel quality driven data rate (CQDDR)                    
          Paging parameter negotiation                                
          Power control            
          Broadcast Encryption     
          Enhanced inquiry scan    
          Interlaced inquiry scan  
          Interlaced page scan     
          RSSI with inquiry results                                   
          AFH capable slave        
          AFH classification slave                                    
          Sniff subrating          
          Pause encryption         
          AFH capable master       
          AFH classification master                                   
          Extended Inquiry Response                                   
          Secure Simple Pairing    
          Encapsulated PDU         
          Non-flushable Packet Boundary Flag                          
          Link Supervision Timeout Changed Event                      
          Inquiry TX Power Level   
          Enhanced Power Control   
          Extended features                                                                                                       [111/1847]
< HCI Command: Read R.. (0x01|0x001c) plen 3  #599 [hci0] 167.180913                                                                        
        Handle: 12                                                                                                                          
        Page: 1                                                                                                                             
> HCI Event: Command Status (0x0f) plen 4     #600 [hci0] 167.181220                                                                        
      Read Remote Extended Features (0x01|0x001c) ncmd 1                                                                                    
        Status: Success (0x00)                                                                                                              
> HCI Event: Read Remote Ex.. (0x23) plen 13  #601 [hci0] 167.181289                                                                        
        Status: Success (0x00)                                                                                                              
        Handle: 12                                                                                                                          
        Page: 1/1                  
        Features: 0x01 0x00 0x00 0x00 0x00 0x00 0x00 0x00             
          Secure Simple Pairing (Host Support)                        
< HCI Command: Remot.. (0x01|0x0019) plen 10  #602 [hci0] 167.181337  
        Address: 20:20:01:1E:56:FF (OUI 20-20-01)                     
        Page scan repetition mode: R2 (0x02)                          
        Page scan mode: Mandatory (0x00)                              
        Clock offset: 0x0000       
> HCI Event: Command Status (0x0f) plen 4     #603 [hci0] 167.181686  
      Remote Name Request (0x01|0x0019) ncmd 1                        
        Status: Success (0x00)     
> HCI Event: Max Slots Change (0x1b) plen 3   #604 [hci0] 167.182313  
        Handle: 12                 
        Max slots: 5               
> HCI Event: Remote Name R.. (0x07) plen 255  #605 [hci0] 167.196899  
        Status: Success (0x00)     
        Address: 20:20:01:1E:56:FF (OUI 20-20-01)                     
        Name: Bluetooth 3.0 Keyboard                                  
@ MGMT Event: Device... (0x000b) plen 42  {0x0001} [hci0] 167.196956  
        BR/EDR Address: 20:20:01:1E:56:FF (OUI 20-20-01)              
        Flags: 0x00000000          
        Data length: 29            
        Name (complete): Bluetooth 3.0 Keyboard                       
        Class: 0x002540            
          Major class: Peripheral (mouse, joystick, keyboards)        
          Minor class: 0x10        
          Limited Discoverable Mode                                   
< HCI Command: Authen.. (0x01|0x0011) plen 2  #606 [hci0] 167.196993  
        Handle: 12                 
> HCI Event: Command Status (0x0f) plen 4     #607 [hci0] 167.197267                                                               [72/1847]
      Authentication Requested (0x01|0x0011) ncmd 1                   
        Status: Success (0x00)     
> HCI Event: Link Key Request (0x17) plen 6   #608 [hci0] 167.197353  
        Address: 20:20:01:1E:56:FF (OUI 20-20-01)                     
< HCI Command: Link K.. (0x01|0x000c) plen 6  #609 [hci0] 167.197383  
        Address: 20:20:01:1E:56:FF (OUI 20-20-01)                     
> HCI Event: Command Complete (0x0e) plen 10  #610 [hci0] 167.197608  
      Link Key Request Negative Reply (0x01|0x000c) ncmd 1            
        Status: Success (0x00)     
        Address: 20:20:01:1E:56:FF (OUI 20-20-01)                     
> HCI Event: IO Capability R.. (0x31) plen 6  #611 [hci0] 167.197632  
        Address: 20:20:01:1E:56:FF (OUI 20-20-01)                     
< HCI Command: IO Cap.. (0x01|0x002b) plen 9  #612 [hci0] 167.197664  
        Address: 20:20:01:1E:56:FF (OUI 20-20-01)                     
        IO capability: DisplayYesNo (0x01)                            
        OOB data: Authentication data not present (0x00)              
        Authentication: Dedicated Bonding - MITM required (0x03)      
> HCI Event: Command Complete (0x0e) plen 10  #613 [hci0] 167.197967  
      IO Capability Request Reply (0x01|0x002b) ncmd 1                
        Status: Success (0x00)     
        Address: 20:20:01:1E:56:FF (OUI 20-20-01)                     
> HCI Event: IO Capability R.. (0x32) plen 9  #614 [hci0] 167.202306  
        Address: 20:20:01:1E:56:FF (OUI 20-20-01)                     
        IO capability: NoInputNoOutput (0x03)                         
        OOB data: Authentication data not present (0x00)              
        Authentication: General Bonding - MITM not required (0x04)    
> HCI Event: User Confirmat.. (0x33) plen 10  #615 [hci0] 167.433216  
        Address: 20:20:01:1E:56:FF (OUI 20-20-01)                     
        Passkey: 933746            
< HCI Command: User C.. (0x01|0x002c) plen 6  #616 [hci0] 167.433308  
        Address: 20:20:01:1E:56:FF (OUI 20-20-01)                     
> HCI Event: Command Complete (0x0e) plen 10  #617 [hci0] 167.435394  
      User Confirmation Request Reply (0x01|0x002c) ncmd 1            
        Status: Success (0x00)     
        Address: 20:20:01:1E:56:FF (OUI 20-20-01)                     
> HCI Event: Simple Pairing... (0x36) plen 7  #618 [hci0] 167.473013  
        Status: Success (0x00)     
        Address: 20:20:01:1E:56:FF (OUI 20-20-01)                     
        Link key: d72bdd17a4a95dd67b2fe0f0f075fa9c                                                                                 [31/1847]
        Key type: Unauthenticated Combination key from P-192 (0x04)   
@ MGMT Event: New Lin.. (0x0009) plen 26  {0x0001} [hci0] 167.509748  
        Store hint: Yes (0x01)     
        BR/EDR Address: 20:20:01:1E:56:FF (OUI 20-20-01)              
        Key type: Unauthenticated Combination key from P-192 (0x04)   
        Link key: d72bdd17a4a95dd67b2fe0f0f075fa9c                    
        PIN length: 0              
> HCI Event: Auth Complete (0x06) plen 3      #620 [hci0] 167.509593  
        Status: Success (0x00)     
        Handle: 12                 
< HCI Command: Set Co.. (0x01|0x0013) plen 3  #621 [hci0] 167.509881  
        Handle: 12                 
        Encryption: Enabled (0x01)                                    
> HCI Event: Command Status (0x0f) plen 4     #622 [hci0] 167.510191  
      Set Connection Encryption (0x01|0x0013) ncmd 1                  
        Status: Success (0x00)     
> HCI Event: Encryption Change (0x08) plen 4  #623 [hci0] 167.530687  
        Status: Success (0x00)     
        Handle: 12                 
        Encryption: Enabled with E0 (0x01)                            
< HCI Command: Read E.. (0x05|0x0008) plen 2  #624 [hci0] 167.530765  
        Handle: 12                 
> HCI Event: Command Complete (0x0e) plen 7   #625 [hci0] 167.531052  
      Read Encryption Key Size (0x05|0x0008) ncmd 1                   
        Status: Success (0x00)     
        Handle: 12                 
        Key size: 16               
@ MGMT Event: Command.. (0x0001) plen 10  {0x0001} [hci0] 167.531133  
      Pair Device (0x0019) plen 7  
        Status: Success (0x00)     
        BR/EDR Address: 20:20:01:1E:56:FF (OUI 20-20-01)              
< ACL Data TX: Handle 12 flags 0x00 dlen 10   #626 [hci0] 167.531164  
      L2CAP: Information Request (0x0a) ident 1 len 2                 
        Type: Extended features supported (0x0002)                    
> ACL Data RX: Handle 12 flags 0x02 dlen 16   #627 [hci0] 167.543550  
      L2CAP: Information Response (0x0b) ident 1 len 8                
        Type: Extended features supported (0x0002)                    
        Result: Success (0x0000)   
        Features: 0x00000280       
          Fixed Channels           
          Unicast Connectionless Data Reception                       
< ACL Data TX: Handle 12 flags 0x00 dlen 10   #628 [hci0] 167.543685  
      L2CAP: Information Request (0x0a) ident 2 len 2                 
        Type: Fixed channels supported (0x0003)                       
> HCI Event: Number of Compl.. (0x13) plen 5  #629 [hci0] 167.546100  
        Num handles: 1             
        Handle: 12                 
        Count: 2                   
> ACL Data RX: Handle 12 flags 0x02 dlen 20   #630 [hci0] 167.547304  
      L2CAP: Information Response (0x0b) ident 2 len 12               
        Type: Fixed channels supported (0x0003)                       
        Result: Success (0x0000)   
        Channels: 0x0000000000000006                                  
          L2CAP Signaling (BR/EDR)                                    
          Connectionless reception                                    
< HCI Command: Discon.. (0x01|0x0006) plen 3  #631 [hci0] 169.545261  
        Handle: 12                 
        Reason: Remote User Terminated Connection (0x13)              
> HCI Event: Command Status (0x0f) plen 4     #632 [hci0] 169.545690  
      Disconnect (0x01|0x0006) ncmd 1                                 
        Status: Success (0x00)     
> HCI Event: Disconnect Comp.. (0x05) plen 4  #633 [hci0] 169.639826  
        Status: Success (0x00)     
        Handle: 12                 
        Reason: Connection Terminated By Local Host (0x16)            
@ MGMT Event: Device D.. (0x000c) plen 8  {0x0001} [hci0] 169.639966  
        BR/EDR Address: 20:20:01:1E:56:FF (OUI 20-20-01)              
        Reason: Connection terminated by local host (0x02)            


```

```


> HCI Event: Connect Request (0x04) plen 10   #1783 [hci0] 324.062214                                                             [130/1864]
        Address: 20:20:01:1E:56:FF (OUI 20-20-01)                                                                                           
        Class: 0x000540                                                                                                                     
          Major class: Peripheral (mouse, joystick, keyboards)                                                                              
          Minor class: 0x10                                                                                                                 
        Link type: ACL (0x01)                                                                                                               
< HCI Command: Accept.. (0x01|0x0009) plen 7  #1784 [hci0] 324.062433                                                                       
        Address: 20:20:01:1E:56:FF (OUI 20-20-01)                                                                                           
        Role: Slave (0x01)                                                                                                                  
> HCI Event: Command Status (0x0f) plen 4     #1785 [hci0] 324.062727                                                                       
      Accept Connection Request (0x01|0x0009) ncmd 1                                                                                        
        Status: Success (0x00)                                                                                                              
> HCI Event: Connect Complete (0x03) plen 11  #1786 [hci0] 324.282190                                                                       
        Status: Success (0x00)                                                                                                              
        Handle: 11                                                                                                                          
        Address: 20:20:01:1E:56:FF (OUI 20-20-01)                                                                                           
        Link type: ACL (0x01)                                                                                                               
        Encryption: Disabled (0x00)                                                                                                         
< HCI Command: Read R.. (0x01|0x001b) plen 2  #1787 [hci0] 324.282649                                                                       
        Handle: 11                                                                                                                          
> HCI Event: Command Status (0x0f) plen 4     #1788 [hci0] 324.283000                                                                       
      Read Remote Supported Features (0x01|0x001b) ncmd 1                                                                                   
        Status: Success (0x00)                                                                                                              
> HCI Event: Read Remote Su.. (0x0b) plen 11  #1789 [hci0] 324.283078                                                                       
        Status: Success (0x00)                                                                                                              
        Handle: 11                                                                                                                          
        Features: 0xbf 0x06 0x86 0x78 0x18 0x1e 0x59 0x87                                                                                   
          3 slot packets                                                                                                                    
          5 slot packets                                                                                                                    
          Encryption                                                                                                                        
          Slot offset                                                                                                                       
          Timing accuracy                                                                                                                   
          Role switch                                                                                                                       
          Sniff mode                                                                                                                        
          Power control requests                                                                                                            
          Channel quality driven data rate (CQDDR)
          Paging parameter negotiation
          Power control
          Broadcast Encryption
          Enhanced inquiry scan                                                                                                    [91/1864]
          Interlaced inquiry scan
          Interlaced page scan
          RSSI with inquiry results 
          AFH capable slave
          AFH classification slave
          Sniff subrating
          Pause encryption
          AFH capable master
          AFH classification master 
          Extended Inquiry Response 
          Secure Simple Pairing
          Encapsulated PDU
          Non-flushable Packet Boundary Flag
          Link Supervision Timeout Changed Event
          Inquiry TX Power Level
          Enhanced Power Control
          Extended features
< HCI Command: Read R.. (0x01|0x001c) plen 3  #1790 [hci0] 324.283142
        Handle: 11
        Page: 1                    
> HCI Event: Max Slots Change (0x1b) plen 3   #1791 [hci0] 324.283425
        Handle: 11
        Max slots: 5
> HCI Event: Command Status (0x0f) plen 4     #1792 [hci0] 324.285012
      Read Remote Extended Features (0x01|0x001c) ncmd 1
        Status: Success (0x00)
> HCI Event: Read Remote Ex.. (0x23) plen 13  #1793 [hci0] 324.285138
        Status: Success (0x00)
        Handle: 11
        Page: 1/1                  
        Features: 0x01 0x00 0x00 0x00 0x00 0x00 0x00 0x00
          Secure Simple Pairing (Host Support)
< HCI Command: Remot.. (0x01|0x0019) plen 10  #1794 [hci0] 324.285385
        Address: 20:20:01:1E:56:FF (OUI 20-20-01)
        Page scan repetition mode: R2 (0x02)
        Page scan mode: Mandatory (0x00)
        Clock offset: 0x0000
< ACL Data TX: Handle 11 flags 0x00 dlen 10   #1795 [hci0] 324.285433
      L2CAP: Information Request (0x0a) ident 1 len 2                                                                              [52/1864]
        Type: Extended features supported (0x0002)
> HCI Event: Command Status (0x0f) plen 4     #1796 [hci0] 324.286695
      Remote Name Request (0x01|0x0019) ncmd 1
        Status: Success (0x00)
> HCI Event: Link Supervisio.. (0x38) plen 4  #1797 [hci0] 324.490891
        Handle: 11
        Timeout: 20000.000 msec (0x7d00)
> ACL Data RX: Handle 11 flags 0x02 dlen 16   #1798 [hci0] 324.492090
      L2CAP: Information Response (0x0b) ident 1 len 8
        Type: Extended features supported (0x0002)
        Result: Success (0x0000)
        Features: 0x00000280
          Fixed Channels
          Unicast Connectionless Data Reception
< ACL Data TX: Handle 11 flags 0x00 dlen 10   #1799 [hci0] 324.492188
      L2CAP: Information Request (0x0a) ident 2 len 2
        Type: Fixed channels supported (0x0003)
> HCI Event: Link Key Request (0x17) plen 6   #1800 [hci0] 324.493542
        Address: 20:20:01:1E:56:FF (OUI 20-20-01)
< HCI Command: Link... (0x01|0x000b) plen 22  #1801 [hci0] 324.493658
        Address: 20:20:01:1E:56:FF (OUI 20-20-01)
        Link key: d72bdd17a4a95dd67b2fe0f0f075fa9c
> HCI Event: Command Complete (0x0e) plen 10  #1802 [hci0] 324.494895
      Link Key Request Reply (0x01|0x000b) ncmd 1
        Status: Success (0x00)
        Address: 20:20:01:1E:56:FF (OUI 20-20-01)
> ACL Data RX: Handle 11 flags 0x02 dlen 20   #1803 [hci0] 324.560932
      L2CAP: Information Response (0x0b) ident 2 len 12
        Type: Fixed channels supported (0x0003)
        Result: Success (0x0000)
        Channels: 0x0000000000000006
          L2CAP Signaling (BR/EDR)
          Connectionless reception
> HCI Event: Number of Compl.. (0x13) plen 5  #1804 [hci0] 324.560962
        Num handles: 1
        Handle: 11
        Count: 2                   
> HCI Event: Inquiry Complete (0x01) plen 1   #1805 [hci0] 324.567927
        Status: Success (0x00)                                                                                                     [13/1864]
@ MGMT Event: Discovering (0x0013) plen 2  {0x0001} [hci0] 324.568074
        Address type: 0x07
          BR/EDR                   
          LE Public
          LE Random
        Discovery: Disabled (0x00)
> HCI Event: Remote Name R.. (0x07) plen 255  #1806 [hci0] 324.571134
        Status: Success (0x00)
        Address: 20:20:01:1E:56:FF (OUI 20-20-01)
        Name: Bluetooth 3.0 Keyboard
@ MGMT Event: Device C.. (0x000b) plen 42  {0x0001} [hci0] 324.571216
        BR/EDR Address: 20:20:01:1E:56:FF (OUI 20-20-01)
        Flags: 0x00000000
        Data length: 29
        Name (complete): Bluetooth 3.0 Keyboard
        Class: 0x000540
          Major class: Peripheral (mouse, joystick, keyboards)
          Minor class: 0x10
> HCI Event: Encryption Change (0x08) plen 4  #1807 [hci0] 324.583667
        Status: Success (0x00)
        Handle: 11
        Encryption: Enabled with E0 (0x01)
< HCI Command: Read E.. (0x05|0x0008) plen 2  #1808 [hci0] 324.583829
        Handle: 11
> HCI Event: Command Complete (0x0e) plen 7   #1809 [hci0] 324.584076
      Read Encryption Key Size (0x05|0x0008) ncmd 1
        Status: Success (0x00)
        Handle: 11
        Key size: 16
> ACL Data RX: Handle 11 flags 0x02 dlen 12   #1810 [hci0] 324.593352
      L2CAP: Connection Request (0x02) ident 2 len 4
        PSM: 17 (0x0011)
        Source CID: 64
< ACL Data TX: Handle 11 flags 0x00 dlen 16   #1811 [hci0] 324.593490
      L2CAP: Connection Response (0x03) ident 2 len 8
        Destination CID: 0
        Source CID: 64
        Result: Connection refused - PSM not supported (0x0002)
        Status: No further information available (0x0000)
> HCI Event: Number of Compl.. (0x13) plen 5  #1812 [hci0] 324.672793
        Num handles: 1
        Handle: 11
        Count: 1                   
> HCI Event: Disconnect Comp.. (0x05) plen 4  #1813 [hci0] 324.672850
        Status: Success (0x00)
        Handle: 11
        Reason: Remote User Terminated Connection (0x13)
@ MGMT Event: Device Di.. (0x000c) plen 8  {0x0001} [hci0] 324.672943
        BR/EDR Address: 20:20:01:1E:56:FF (OUI 20-20-01)
        Reason: Connection terminated by remote host (0x03)






```


Any idea how to fix this?

---

### Post by hoijtink on 2020-10-30
Not sure, but maybe this is the same issue of the XBOX controller pairing, but then not properly connecting. Check out this site for permanently changing the bluetooth option:

[https://www.forbes.com/sites/jasonevangelho/2019/10/14/linux-gaming-tip-how-to-pair-your-xbox-one-s-and-switch-pro-controllers-via-bluetooth/](https://www.forbes.com/sites/jasonevangelho/2019/10/14/linux-gaming-tip-how-to-pair-your-xbox-one-s-and-switch-pro-controllers-via-bluetooth/)

---

### Post by jordana2 on 2020-10-31
thank you so much - this indeed made my bluetooth keyboard connect :p

---

### Post by jordana2 on 2020-10-31
well, it seems that this might not have solved anything... I might have just been happy too soon with a fresh install. now it fails the same way again. quite a few red alarms in bluetooth.service

```


jordana@dad-pi4g:~$ systemctl status bluetooth.service 
&#9679; bluetooth.service - Bluetooth service
     Loaded: loaded (/lib/systemd/system/bluetooth.service; enabled; vendor preset: enabled)
     Active: active (running) since Sat 2020-10-31 09:39:56 GMT; 1min 17s ago
       Docs: man:bluetoothd(8)
   Main PID: 703 (bluetoothd)
     Status: "Running"
      Tasks: 1 (limit: 4145)
     CGroup: /system.slice/bluetooth.service
             &#9492;&#9472;703 /usr/lib/bluetooth/bluetoothd

Oct 31 09:39:56 dad-pi4g bluetoothd[703]: src/main.c:parse_controller_config() Key file does not have group “Controller”
Oct 31 09:39:56 dad-pi4g systemd[1]: Started Bluetooth service.
Oct 31 09:39:56 dad-pi4g bluetoothd[703]: Starting SDP server
Oct 31 09:39:56 dad-pi4g bluetoothd[703]: Bluetooth management interface 1.17 initialized
Oct 31 09:39:57 dad-pi4g bluetoothd[703]: profiles/audio/avctp.c:avctp_server_socket() setsockopt(L2CAP_OPTIONS): Invalid argument (22)
Oct 31 09:39:57 dad-pi4g bluetoothd[703]: avrcp-controller: Protocol not supported (93)
Oct 31 09:39:57 dad-pi4g bluetoothd[703]: profiles/audio/avctp.c:avctp_server_socket() setsockopt(L2CAP_OPTIONS): Invalid argument (22)
Oct 31 09:39:57 dad-pi4g bluetoothd[703]: audio-avrcp-target: Protocol not supported (93)
Oct 31 09:40:01 dad-pi4g bluetoothd[703]: Endpoint registered: sender=:1.37 path=/MediaEndpoint/A2DPSink/sbc
Oct 31 09:40:01 dad-pi4g bluetoothd[703]: Endpoint registered: sender=:1.37 path=/MediaEndpoint/A2DPSource/sbc


```

just as a reference I have no issue using my bluetooth keyboard with Raspberry Pi OS.

---

### Post by jordana2 on 2020-11-12
I observed Controller AA:AA:AA:AA:AA:AA under bluetoothctl. Restarting bluetooth service cures the issue:

```

jordana@dad-pi4g:~$ sudo bluetoothctl
Agent registered
[CHG] Controller AA:AA:AA:AA:AA:AA Pairable: yes
[bluetooth]# exit
jordana@dad-pi4g:~$ sudo systemctl restart bluetooth
jordana@dad-pi4g:~$ sudo hciconfig hci0 up
jordana@dad-pi4g:~$ sudo bluetoothctl
Agent registered
[CHG] Controller B8:27:EB:EC:D3:42 Pairable: yes
[bluetooth]#

```

Anybody has a suggestion what to check further when Controller is AA:AA:AA:AA:AA:AA ?

---

### Post by jordana2 on 2020-11-12
adding 
```

@reboot sudo systemctl restart bluetooth

```
at the end of crontab -e seems to be an effective workaround

---

### Post by jordana2 on 2020-11-13
found a bug opened for this [https://bugs.launchpad.net/ubuntu/+source/pi-bluetooth/+bug/1901272](https://bugs.launchpad.net/ubuntu/+source/pi-bluetooth/+bug/1901272)

tried the PPA advised in this bug and it solved my issue.

interestingly the controller address is different:

```

jordana@dad-pi4g:~$ sudo bluetoothctl
Agent registered
[CHG] Controller DC:A6:32:A2:0B:85 Pairable: yes
[CHG] Device 20:20:01:1E:56:FF Connected: yes
[Bluetooth 3.0 Keyboard]#

```

---

