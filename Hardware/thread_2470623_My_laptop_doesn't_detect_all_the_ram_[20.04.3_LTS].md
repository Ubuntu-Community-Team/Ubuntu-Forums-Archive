---
title: "My laptop doesn't detect all the ram [20.04.3 LTS]"
date: 2022-01-05
forum: Hardware
---

### Post by surrealvessel on 2022-01-05
I recently switched to ubuntu 20.04.3 LTS. I had never used linux before but everything worked fine.


After using it a bit I decided to re-install it but now to establish partitions, but after the installation ubuntu did not start, so I reinstalled it again but now with the automatic partitions, but again it does not start.
I'm a newbie at this, so I did a little searching on the internet and I managed to fix it by moving a few things in the BIOS, but now the system monitor says I have 1.8 Gb of RAM when I actually have 4 Gb.


```
$ sudo dmidecode | less
```
Output:
```
# dmidecode 3.2
Getting SMBIOS data from sysfs.
SMBIOS 2.7 present.


Handle 0x0005, DMI type 6, 12 bytes
Memory Module Information
        Socket Designation: DIMM0
        Bank Connections: 0 0
        Current Speed: Unknown
        Type: None
        Installed Size: 2048 MB (Single-bank Connection)
        Enabled Size: 2048 MB (Single-bank Connection)
        Error Status: OK


Handle 0x0006, DMI type 6, 12 bytes
Memory Module Information
        Socket Designation: DIMM1
        Bank Connections: 0 0
        Current Speed: Unknown
        Type: None
        Installed Size: Not Installed
        Enabled Size: Not Installed

        Error Status: OK

```



[IMG]https://ubuntuforums.org/attachment.php?attachmentid=289743&stc=1[/IMG]

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=289744&stc=1[/IMG]


In the two images the system says that I have 1.8 GB but it should have 4 GB.
I think my laptop only detects one stick of RAM. Pls help me.


SOLVED:Unplug and reconnect the RAM and now it works.

---

### Post by The Cog on 2022-01-05
It might be interesting to see what **[FONT=Courier New][COLOR="#B22222"]sudo lshw -C memory[/COLOR][/FONT]** says.

---

### Post by TheFu on 2022-01-05
Does the BIOS see all the RAM?
How much RAM is the iGPU stealing?  Some will take up to 4GB of RAM. Many BIOS configs will let us control how much RAM is taken to be used by the iGPU.

I find the output from 
```
sudo inxi -mxx
```
to be easier to understand.

Or there is 
```
free -mh
```
or
```
more /proc/meminfo
```

---

### Post by QIII on 2022-01-05
I think this may be the key:

```
        Installed Size: Not Installed
        Enabled Size: Not Installed
```

The motherboard is reporting to the OS that there is no memory in bank 1.  Have opened the machine to wiggle the module and make sure it is seated properly?

---

### Post by surrealvessel on 2022-01-05
> **The Cog said:**
> It might be interesting to see what **[FONT=Courier New][COLOR=#B22222]sudo lshw -C memory[/COLOR][/FONT]** says.

Here it is

```
*-memory      
       descripción: Memoria de sistema
       id físico: f
       ranura: Placa de sistema o placa base
       tamaño: 2GiB
     *-bank:0
          descripción: SODIMM DDR3 Síncrono 1333 MHz (0.8 ns)
          producto: ACR16D3LFS1KBG/2G
          fabricante: Kingston
          id físico: 0
          serie: 22381021
          ranura: DIMM0
          tamaño: 2GiB
          anchura: 64 bits
          reloj: 1333MHz (0.8ns)
     *-bank:1
          descripción: SODIMMProject-Id-Version: lshwReport-Msgid-Bugs-To: FULL NAME <EMAIL@ADDRESS>PO-Revision-Date: 2012-03-14 06:38+0000Last-Translator: Paco Molinero <paco@byasl.com>Language-Team: Spanish <es@li.org>MIME-Version: 1.0Content-Type: text/plain; charset=UTF-8Content-Transfer-Encoding: 8bitX-Launchpad-Export-Date: 2021-08-02 16:47+0000X-Generator: Launchpad (build 8bd362bf86c4b35e805f897f03c203e3576a7006) [vacío]
          id físico: 1
          ranura: DIMM1
```

Some things are in Spanish because I'm from Mexico.

---

