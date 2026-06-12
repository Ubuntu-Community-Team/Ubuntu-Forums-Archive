---
title: "HP Printer"
date: 2009-08-11
forum: Hardware
---

### Post by allstar1971 on 2009-08-11
I hope I am in the correct forum.

I have read tons of threads regarding Jaunty printing issues and I am not sure if I have had this problem solved.

I have an HP Laserjet 8000 with PS that I use for my desktop publishing business.

When I print one page, it prints fine and fast.
When I print 2 pages of an item, it prints four.
When I print 3 pages of an item, it prints nine.

I have gone as far as six copies of a page and it prints 36.

I have HPLIP installed and installed the printer via the system-config-printer 1.1.3.

What is the issue or do I have to live with it? I have tried Suse, PCLinuxOS and neither have this issue.

I love Ubuntu and would not like to switch distros. But I am afraid I might 'forget' and try printing 50 pages which would be a total disaster.

Any help would be appreciated. (HP-setup info is below)

:confused:

HP Linux Imaging and Printing System (ver. 3.9.2)
Printer/Fax Setup Utility ver. 8.0

Copyright (c) 2001-9 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.


Installs HPLIP printers and faxes in the CUPS spooler. Tries to automatically determine the correct PPD file to use. Allows the printing of a testpage. Performs basic fax parameter setup.

Usage: hp-setup [MODE] [OPTIONS] [SERIAL NO.|USB bus:device|IP|DEVNODE]

[MODE]
  Run in graphical    -u or --gui (Default)                                 
  UI mode:                                                                  
  Run in interactive  -i or --interactive                                   
  mode:                                                                     

[OPTIONS]
  Automatic mode:     -a or --auto (-i mode only)                           
  To specify the      --port=<port> (Valid values are 1*, 2, and 3.         
  port on a           *default)                                             
  multi-port                                                                
  JetDirect:                                                                
  No testpage in      -x (-i mode only)                                     
  automatic mode:                                                           
  To specify a CUPS   -p<printer> or --printer=<printer> (-i mode only)     
  printer queue                                                             
  name:                                                                     
  To specify a CUPS   -f<fax> or --fax=<fax> (-i mode only)                 
  fax queue name:                                                           
  Type of queue(s)    -t<typelist> or --type=<typelist>. <typelist>: print*,
  to install:         fax* (*default) (-i mode only)                        
  To specify the      -d<device> or --device=<device> (--qt4 mode only)     
  device URI to                                                             
  install:                                                                  
  Set the language:   -q <lang> or --lang=<lang>. Use -q? or --lang=? to see
                      a list of available language codes.                   
  Set the logging     -l<level> or --logging=<level>                        
  level:                                                                    
                      <level>: none, info*, error, warn, debug (*default)   
  Run in debug mode:  -g (same as option: -ldebug)                          
  This help           -h or --help                                          
  information:                                                              

[SERIAL NO.|USB ID|IP|DEVNODE]
  USB bus:device      "xxx:yyy" where 'xxx' is the USB bus and 'yyy' is the 
  (usb only):         USB device. (Note: The ':' and all leading zeros must 
                      be present.)                                          
                      Use the 'lsusb' command to obtain this information.   
  IPs (network        IPv4 address "a.b.c.d" or "hostname"                  
  only):                                                                    
  DEVNODE (parallel   "/dev/parportX", X=0,1,2,...                          
  only):                                                                    
  SERIAL NO. (usb     "serial no."                                          
  and parallel                                                              
  only):                                                                    

Examples:
  Setup using GUI     $ hp-setup                                            
  mode:                                                                     
  Setup using GUI     $ hp-setup -b usb                                     
  mode, specifying                                                          
  usb:                                                                      
  Setup using GUI     $ hp-setup 192.168.0.101                              
  mode, specifying                                                          
  an IP:                                                                    
  One USB printer     $ hp-setup -i -a                                      
  attached,                                                                 
  automatic:                                                                
  USB, IDs            $ hp-setup -i 001:002                                 
  specified:                                                                
  Network:            $ hp-setup -i 66.35.250.209                           
  Network, Jetdirect  $ hp-setup -i --port=2 66.35.250.209                  
  port 2:                                                                   
  Parallel:           $ hp-setup -i /dev/parport0                           
  USB or parallel,    $ hp-setup -i US12345678A                             
  using serial                                                              
  number:                                                                   
  USB, automatic:     $ hp-setup -i --auto 001:002                          
  Parallel,           $ hp-setup -i -a -x /dev/parport0                     
  automatic, no                                                             
  testpage:                                                                 
  Parallel, choose    $ hp-setup -i -b par                                  
  device:                                                                   

Notes:
1. If no serial number, USB ID, IP, or device node is specified, the USB and parallel busses will be probed for devices.
2. Using 'lsusb' to obtain USB IDs: (example)
	$ lsusb
	Bus 003 Device 011: ID 03f0:c202 Hewlett-Packard
	$ hp-setup --auto 003:011
	(Note: You may have to run 'lsusb' from /sbin or another location. Use '$ locate lsusb' to determine this.)
3. Parameters -a, -f, -p, or -t are not valid in GUI (-u) mode.

See Also:
hp-makeuri
hp-probe

---

