---
title: "Very high core temperatures - lmsensors"
date: 2009-04-03
forum: Hardware
---

### Post by ashwinhgtx on 2009-04-03
I'm running Kubuntu 8.10 and I have lmsensors installed. I have a Thinkpad R60 with Core Duo 1667MHz processor, 2GB RAM and a 40GB hard drive.
When I run the sensors command this is what I get

```
ashwin@TWINTURBOV8:~$ sensors
acpitz-virtual-0             
Adapter: Virtual device      
temp1:       +59.0°C  (crit = +127.0°C)                  
temp2:       +61.0°C  (crit = +97.0°C)                   

thinkpad-isa-0000
Adapter: ISA adapter
fan1:       2736 RPM
temp1:       +59.0°C                                    
temp2:       +45.0°C                                    
temp3:       +47.0°C                                    
ERROR: Can't get value of subfeature temp4_input: Can't read
temp4:        +0.0°C                                        
temp5:       +40.0°C                                        
ERROR: Can't get value of subfeature temp6_input: Can't read
temp6:        +0.0°C                                        
temp7:       +35.0°C                                        
ERROR: Can't get value of subfeature temp8_input: Can't read
temp8:        +0.0°C
temp9:       +46.0°C
temp10:      +49.0°C
temp11:      +58.0°C
ERROR: Can't get value of subfeature temp12_input: Can't read
temp12:       +0.0°C
ERROR: Can't get value of subfeature temp13_input: Can't read
temp13:       +0.0°C
ERROR: Can't get value of subfeature temp14_input: Can't read
temp14:       +0.0°C
ERROR: Can't get value of subfeature temp15_input: Can't read
temp15:       +0.0°C
ERROR: Can't get value of subfeature temp16_input: Can't read
temp16:       +0.0°C

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +60.0°C  (crit = +100.0°C)

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +61.0°C  (crit = +100.0°C)

```


Is this normal? I only have firefox and konqueror with one tab open each.
When I set BOINC to run all the time Core 0 and Core 1 temperatures are around 76-80°C. CPU usage will be 100% at that time.Once it went to 86°C.

Even otherwise when I am not using BOINC or any CPU intensive programs the temperatures of the cores are above 65°C. Today is the first time I am seeing something as low as 60°C.
Is something wrong with my fan?

---

### Post by ashwinhgtx on 2009-04-03
My temperatures just hit 86°C again. My room mate's R60 with the same configuration running XP rarely goes above 53°C.
Is this a linux problem?

---

### Post by norwoods on 2009-04-03
did you run: sudo sensors-detect
yes, those temps are high.

---

### Post by ashwinhgtx on 2009-04-04
> **norwoods said:**
> did you run: sudo sensors-detect
yes, those temps are high.

Yes I've done it before but I did it again anyway. Here's the output

```
ashwin@TWINTURBOV8:~$ sudo sensors-detect
[sudo] password for ashwin:              
# sensors-detect revision 5249 (2008-05-11 22:56:25 +0200)

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe  
and recommended to accept the default answers to all questions,   
unless you know what you're doing.                                

We can start with probing for (PCI) I2C or SMBus adapters.
Do you want to probe now? (YES/no): y                     
Probing for PCI bus adapters...                           
Use driver `i2c-i801' for device 0000:00:1f.3: Intel 82801G ICH7

We will now try to load each adapter module in turn.
Load `i2c-i801' (say NO if built into your kernel)? (YES/no): y
Module loaded successfully.                                    
If you have undetectable or unsupported I2C/SMBus adapters, you can have
them scanned by manually loading the modules before running this script.

To continue, we need module `i2c-dev' to be loaded.
Do you want to load `i2c-dev' now? (YES/no): y     
Module loaded successfully.                        

We are now going to do the I2C/SMBus adapter probings. Some chips may
be double detected; we choose the one with the highest confidence    
value in that case.                                                  
If you found that the adapter hung after probing a certain address,  
you can specify that address to remain unprobed.                     

Next adapter: SMBus I801 adapter at 18e0 (i2c-0)
Do you want to scan it? (YES/no/selectively): y 

Some chips are also accessible through the ISA I/O ports. We have to
write to arbitrary I/O ports to probe them. This is usually safe though.
Yes, you do have ISA I/O ports even if you do not have any ISA slots!   
Do you want to scan the ISA I/O ports? (YES/no): y                      
Probing for `National Semiconductor LM78' at 0x290...       No          
Probing for `National Semiconductor LM78-J' at 0x290...     No          
Probing for `National Semiconductor LM79' at 0x290...       No          
Probing for `Winbond W83781D' at 0x290...                   No          
Probing for `Winbond W83782D' at 0x290...                   No          
Probing for `IPMI BMC KCS' at 0xca0...                      No          
Probing for `IPMI BMC SMIC' at 0xca8...                     No          

Some Super I/O chips may also contain sensors. We have to write to
standard I/O ports to probe them. This is usually safe.           
Do you want to scan for Super I/O sensors? (YES/no): y            
Probing for Super-I/O at 0x2e/0x2f                                
Trying family `National Semiconductor'...                   No    
Trying family `SMSC'...                                     No    
Trying family `VIA/Winbond/Fintek'...                       No    
Trying family `ITE'...                                      No    
Probing for Super-I/O at 0x4e/0x4f                                
Trying family `National Semiconductor'...                   No    
Trying family `SMSC'...                                     No    
Trying family `VIA/Winbond/Fintek'...                       No    
Trying family `ITE'...                                      No    

Some south bridges, CPUs or memory controllers may also contain
embedded sensors. Do you want to scan for them? (YES/no): y    
Silicon Integrated Systems SIS5595...                       No 
VIA VT82C686 Integrated Sensors...                          No 
VIA VT8231 Integrated Sensors...                            No 
AMD K8 thermal sensors...                                   No 
AMD K10 thermal sensors...                                  No
Intel Core family thermal sensor...                         Success!
    (driver `coretemp')
Intel AMB FB-DIMM thermal sensor...                         No

Now follows a summary of the probes I have just done.
Just press ENTER to continue:

Driver `coretemp' (should be inserted):
  Detects correctly:
  * Chip `Intel Core family thermal sensor' (confidence: 9)

I will now generate the commands needed to load the required modules.
Just press ENTER to continue:

To load everything that is needed, add this to /etc/modules:

#----cut here----
# Chip drivers
coretemp
#----cut here----

Do you want to add these lines automatically? (yes/NO)y

```

---

