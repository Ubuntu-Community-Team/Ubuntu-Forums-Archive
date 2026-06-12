---
title: "What is the KHOIHGIUCCHHII handle?"
date: 2017-07-26
forum: Hardware
---

### Post by ToFue on 2017-07-26
Hello,  I was walking through my laptop's PCI descriptors and ran into this handle:

```
$ sudo dmidecode -u

...

Handle 0x0031, DMI type 133, 5 bytes
        Header and Data:
                85 05 31 00 01
        Strings:
                4B 48 4F 49 48 47 49 55 43 48 48 49 49 00
                "KHOIHGIUCCHHII"
...
```
Does anyone know what KHOIHGIUCCHHII is, exactly?

Of course, this entry also shows up while looking around in a booted UEFI Shell. It appears to be present in most Lenovo PCI dumps (according to duck & google search results), which suggests to me that it is a Lenovo-specific descriptor.. My first assumption is that its the generic EFI *HII interface handle (as per UEFI specification label), though I did see a specifically separate entry for that in the device table while in UEFI shell -  concurrently with this one..  however the generic *HII descriptor appears to missing from the dmidecode dump..  

I apologize if this is a duplicate, but my search results only produced results on the "KHOIHGIUCCHHII" string as part of PCI dumps, and I couldn't track down an actual explanation.. 

I thank you for your replies!

---

### Post by Autodave on 2017-07-27
Just wanted to let you know that you are not being overlooked. I tried early this morning and a little while ago and I cannot find any explanation of what that means.

---

### Post by Yellow Pasque on 2017-07-27
Looks like garbage to me, or perhaps means something to non-English speakers.

```
Types 128 to 255 are for OEM-specific data.  dmidecode will display these entries by default, but it can only decode them when the vendors have contributed documentation or code for them.
```

---

### Post by ToFue on 2017-07-27
@Autodave Thanks, I appreciate that! :)

@Temüjin Based on search results, it does appear that it might be lenovo-specific.

 If it helps, there is also this BIOS language:

```
Handle 0x001F, DMI type 13, 22 bytes
        Header and Data:
                0D 16 1F 00 02 00 00 00 00 00 00 00 00 00 00 00
                00 00 00 00 00 01
        Strings:
                65 6E 7C 55 53 7C 69 73 6F 38 38 35 39 2D 21 00
                "en|US|iso8859-1"
                7A 68 7C 54 57 7C 75 6E 69 63 6F 64 65 00
                "zh|TW|unicode"
```

 I wouldn't have a clue for how to translate it, if it is simplified Chinese... :(

---

### Post by vasa1 on 2017-07-27
According to [https://linux.die.net/man/8/dmidecode](https://linux.die.net/man/8/dmidecode),```
-u, --dump
Do not decode the entries, dump their contents as hexadecimal instead. Note that this is still a text output, 
no binary data will be thrown upon you. The strings attached to each entry are displayed as both hexadecimal 
and ASCII . This option is mainly useful for debugging.
```So why not run without the -u option? Maybe things become clearer?

---

### Post by ToFue on 2017-07-30
> **vasa1 said:**
> According to [https://linux.die.net/man/8/dmidecode](https://linux.die.net/man/8/dmidecode),```
-u, --dump
Do not decode the entries, dump their contents as hexadecimal instead. Note that this is still a text output, 
no binary data will be thrown upon you. The strings attached to each entry are displayed as both hexadecimal 
and ASCII . This option is mainly useful for debugging.
```So why not run without the -u option? Maybe things become clearer?

Your suggestion is intuitive, but omitting the 'dump' flag only dumps the data hex string, skips the K*HII hex, and adds a label about "OEM-specific type" - we lose reported information for objects initialized in memory:
```
$ sudo dmidecode

...

Handle 0x0031, DMI type 133, 5 bytes
OEM-specific Type
        Header and Data:
                85 05 31 00 01
        Strings:
                "KHOIHGIUCCHHII"
...
```

The oem label might almost be useful, but we're given the numeric DMI type in the output, anyway. I include the `-u` flag for thoroughness and readability sake - I like to see both the ascii descriptor string and the raw hex. 

I'm sure you don't need me to explain the following, but I do so as an aside for the sake of other readers: 

The hex represents raw memory values for particular fields of various tables as populated by UEFI during boot. The bootloader or kernel might relocate these tables in memory during efi loading, pam, etc.. Some pointers are further resolved by the system if the kernel has drivers that can address into devices beyond an initial device pointer (if protocols are known to the kernel).  Often times, libraries or other objects are accessed only by a descriptor string (handle) acquired from a table look-up instead of storing that information elsewhere. 

By knowing the hex bytes, we don't need to rely on decoded ascii values, and we can further parse/use raw byte values that ascii might otherwise omit; as 'non-printable' bytes wouldn't show up with ascii alone (like no-ops and other escape characters). This can also provide clues to whether 'strings' are truly strings or in themselves pointers (or could even be clues about table corruption or stack smashing - i.e., malware), etc..

For example: if we only have the ascii string, "Foo Bar" to rely on, we wouldn't know that its value may actually be ```
46 02 90 90 90 6f 6f 90 20 11 90 42 61 72 20 90 02 90 90 0a
``` in hex, and would mistakenly use "46 6f 6f 20 42 61 72 0a" as the string's value instead...

---

### Post by ToFue on 2017-07-30
> **Temüjin said:**
> Looks like garbage to me, or perhaps means something to non-English speakers.

```
Types 128 to 255 are for OEM-specific data.  dmidecode will display these entries by default, but it can only decode them when the vendors have contributed documentation or code for them.
```

Ok, your edit clarifies that a bit - thanks!  

Looks like I'll need to look into the PE option roms .. :(

P.S.:  I tried to reply to your P.M., but you're account might be blocking..?

---

