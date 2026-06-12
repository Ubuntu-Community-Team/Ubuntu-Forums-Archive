---
title: "Useful Hardware commands"
date: 2011-02-01
forum: Hardware
---

### Post by COKEDUDE on 2011-02-01
Are there any other useful hardware commands to get information about your hardware? Is there any information that can't be found with these commands? 

```
cat /proc/cpuinfo
cat /proc/meminfo
dmesg
lspci
sudo dmidecode
cpuid | more
lspci -v | grep VGA
sudo lspci -v -s 00:02.0
sudo lspci -vvv -s 00:02.0
```

---

### Post by cascade9 on 2011-02-01
sudo lshw 

That might show you some thing that arent in the commands above.

---

### Post by COKEDUDE on 2011-02-01
> **cascade9 said:**
> sudo lshw 

That might show you some thing that arent in the commands above.

Is lshw a more compact version of dmidecode? It seems like they show the same thing.

---

### Post by Megaptera on 2011-02-02
> **COKEDUDE said:**
> Are there any other useful hardware commands to get information about your hardware? Is there any information that can't be found with these commands? 

You might have a look at CLI Companion. Description from Launchpad:
"CLI Companion is a tool to store and run Terminal commands from a GUI. People unfamiliar with the Terminal will find CLI Companion a useful way to become acquainted with the Terminal and unlock its potential. Experienced users can use CLI Companion to store their extensive list of commands in a searchable list."

[https://launchpad.net/clicompanion](https://launchpad.net/clicompanion)

---

### Post by cascade9 on 2011-02-02
> **COKEDUDE said:**
> Is lshw a more compact version of dmidecode? It seems like they show the same thing.

lshw uses  at least some code from dmidecode. I'm prettty sure its got code that is specific to lshw, so while they might look like they have very similar outputs, its possible that if you looked around enough you would find some setups that would have different reports from lshw vs demidecode.

---

### Post by COKEDUDE on 2011-02-02
> **Megaptera said:**
> You might have a look at CLI Companion. Description from Launchpad:
"CLI Companion is a tool to store and run Terminal commands from a GUI. People unfamiliar with the Terminal will find CLI Companion a useful way to become acquainted with the Terminal and unlock its potential. Experienced users can use CLI Companion to store their extensive list of commands in a searchable list."

[https://launchpad.net/clicompanion](https://launchpad.net/clicompanion)

Thats a really cool program. I am ALWAYS searching through my .bash_history for commands that I don't use very often.

---

### Post by mc4man on 2011-02-02
A different way to see the lshw (thru internet browser), is to go like this, look in home dir.
```
sudo lshw -html >  hardware.html
```

While there are different ways to do this or variations of,  for retrieving bash history I like this in home dir,  then type a few letters, word(s), whatever in terminal and use the page up or down keys.

make file named  .inputrc

```
"\e[5~": history-search-backward
"\e[6~": history-search-forward
```

---

### Post by COKEDUDE on 2011-02-02
> **mc4man said:**
> A different way to see the lshw (thru internet browser), is to go like this, look in home dir.
```
sudo lshw -html >  hardware.html
```

While there are different ways to do this or variations of,  for retrieving bash history I like this in home dir,  then type a few letters, word(s), whatever in terminal and use the page up or down keys.

make file named  .inputrc

```
"\e[5~": history-search-backward
"\e[6~": history-search-forward
```

Cool. Thx for pointing that out.

---

### Post by cascade9 on 2011-02-02
> **mc4man said:**
> A different way to see the lshw (thru internet browser), is to go like this, look in home dir.

Another way is gtk-lshw.

---

### Post by duanedesign on 2011-02-02
> **COKEDUDE said:**
> Thats a really cool program. I am ALWAYS searching through my .bash_history for commands that I don't use very often.

That was my main motivation for making this program. A lot of people new to the Terminal have found it useful to get acquainted with commands but that is only one audience for this app, IMHO. I hope people familiar with the Terminal find this application useful as well.

Let me know what you think. if you have any suggestions or find a bug [let me know]("https://launchpad.net/clicompanion").

thank you,
duanedesign

---

### Post by Megaptera on 2011-02-04
> **COKEDUDE said:**
> Thats a really cool program. I am ALWAYS searching through my .bash_history for commands that I don't use very often.

Glad it's useful! :p

---

### Post by COKEDUDE on 2011-02-04
> **cascade9 said:**
> lshw uses  at least some code from dmidecode. I'm prettty sure its got code that is specific to lshw, so while they might look like they have very similar outputs, its possible that if you looked around enough you would find some setups that would have different reports from lshw vs demidecode.

I found a perfect example of what you are talking about. Most people are not going to be able to tell that 2 of the DIMM slots are empty from reading dmidecode. I guessed that from reading the manufacturer number and the serial number. I have never seen a serial number or manufacturer number that were all the same letters. I now no that's what the mean by **No Module Installed**. It would have been nice to give a more useful message. This was very obvious from the **lshw** command. 

```
$ sudo dmidecode --type 17
# dmidecode 2.11
SMBIOS 2.4 present.

Handle 0x0032, DMI type 17, 27 bytes
Memory Device
        Array Handle: 0x0031
        Error Information Handle: Not Provided
        Total Width: 64 bits
        Data Width: 64 bits
        Size: No Module Installed
        Form Factor: DIMM
        Set: None
        Locator: DIMM_4
        Bank Locator: Not Specified
        Type: Unknown
        Type Detail: Synchronous
        Speed: Unknown
        Manufacturer: FFFFFFFFFFFFFFFF
        Serial Number: FFFFFFFF
        Asset Tag: Not Specified
        Part Number:                   

Handle 0x0033, DMI type 17, 27 bytes
Memory Device
        Array Handle: 0x0031
        Error Information Handle: Not Provided
        Total Width: 64 bits
        Data Width: 64 bits
        Size: No Module Installed
        Form Factor: DIMM
        Set: None
        Locator: DIMM_3
        Bank Locator: Not Specified
        Type: Unknown
        Type Detail: Synchronous
        Speed: Unknown
        Manufacturer: FFFFFFFFFFFFFFFF
        Serial Number: FFFFFFFF
        Asset Tag: Not Specified
        Part Number:                   

Handle 0x0034, DMI type 17, 27 bytes
Memory Device
        Array Handle: 0x0031
        Error Information Handle: Not Provided
        Total Width: 64 bits
        Data Width: 64 bits
        Size: 1024 MB
        Form Factor: DIMM
        Set: None
        Locator: DIMM_2
        Bank Locator: Not Specified
        Type: DDR2
        Type Detail: Synchronous
        Speed: 800 MHz
        Manufacturer: AD00000000000000
        Serial Number: 04008076
        Asset Tag: Not Specified
        Part Number: HYMP112U64CP8-S6  

Handle 0x0035, DMI type 17, 27 bytes
Memory Device
        Array Handle: 0x0031
        Error Information Handle: Not Provided
        Total Width: 64 bits
        Data Width: 64 bits
        Size: 1024 MB
        Form Factor: DIMM
        Set: None
        Locator: DIMM_1
        Bank Locator: Not Specified
        Type: DDR2
        Type Detail: Synchronous
        Speed: 800 MHz
        Manufacturer: AD00000000000000
        Serial Number: 00006104
        Asset Tag: Not Specified
        Part Number: HYMP112U64CP8-S6  

```

```
~]$ sudo lshw -short -C memory
H/W path    Device      Class       Description
===============================================
/0/1                    memory      128KiB BIOS
/0/2/10                 memory      128KiB L1 cache
/0/2/11                 memory      1MiB L2 cache
/0/31                   memory      2GiB System Memory
/0/31/0                 memory      DIMM Synchronous [empty]
/0/31/1                 memory      DIMM Synchronous [empty]
/0/31/2                 memory      1GiB DIMM DDR2 Synchronous 800 MHz (1.2 ns)
/0/31/3                 memory      1GiB DIMM DDR2 Synchronous 800 MHz (1.2 ns)
/0/0                    memory      RAM memory
/0/0.1                  memory      RAM memory
/0/0.2                  memory      RAM memory
/0/0.3                  memory      RAM memory
/0/0.4                  memory      RAM memory
/0/0.5                  memory      RAM memory
/0/0.6                  memory      RAM memory
/0/0.7                  memory      RAM memory
/0/9                    memory      RAM memory
/0/a.2                  memory      RAM memory

```

> **duanedesign said:**
> That was my main motivation for making this program. A lot of people new to the Terminal have found it useful to get acquainted with commands but that is only one audience for this app, IMHO. I hope people familiar with the Terminal find this application useful as well.

Let me know what you think. if you have any suggestions or find a bug [let me know]("https://launchpad.net/clicompanion").

thank you,
duanedesign

Will do :). Any chance that you can make a rpm package? I have to use Fedora right now cause of a class :(. I only have Ubuntu on a virtualbox right now.

---

### Post by quadproc on 2011-02-04
> **COKEDUDE said:**
> Are there any other useful hardware commands to get information about your hardware?
The hardinfo program is rather comprehensive.  If it isn't already installed then you can get it by using Synaptic or apt-get.

quadproc

---

### Post by AlphaLexman on 2011-02-04
I like:
```
apropos " ls*" | grep ls
```

EDIT: This works even better if you have the alias```
alias grep='grep -i --color=auto'
```
Then the 'ls' is hi-lighted in color!

---

### Post by cascade9 on 2011-02-04
> **COKEDUDE said:**
> I found a perfect example of what you are talking about. Most people are not going to be able to tell that 2 of the DIMM slots are empty from reading dmidecode. I guessed that from reading the manufacturer number and the serial number. I have never seen a serial number or manufacturer number that were all the same letters. I now no that's what the mean by **No Module Installed**. It would have been nice to give a more useful message. This was very obvious from the **lshw** command. 

I thought that there would be at least one decent example, but thanks for the feedback. ;)

---

### Post by COKEDUDE on 2011-07-21
Nobody pointed out free or top to me. Here is my updated list. 

```
cat /proc/cpuinfo
cat /proc/meminfo
dmesg
free
top
lspci
sudo dmidecode
cpuid | more
lspci -v | grep VGA
sudo lspci -v -s 00:02.0
sudo lspci -vvv -s 00:02.0
```

---

### Post by Bob&amp;Frank on 2011-10-01
thanks for the info i was wondering?

how do you,

cat meminfo 

but make it human readable.
and where can i find the man page for meminfo

also how would you make meminfo print out like redhat 
so it looks like top

thanks

---

### Post by COKEDUDE on 2012-03-16
> **Bob&Frank said:**
> thanks for the info i was wondering?

how do you,

cat meminfo 

but make it human readable.
and where can i find the man page for meminfo

also how would you make meminfo print out like redhat 
so it looks like top

thanks

Is this what you are asking? Just cat it like you would any other file. 

```
$ cat /proc/meminfo
MemTotal:        3348304 kB
MemFree:          153000 kB
Buffers:          184828 kB
Cached:           653932 kB
SwapCached:       151816 kB
Active:          2035712 kB
Inactive:        1018400 kB
Active(anon):    1756376 kB
Inactive(anon):   646480 kB
Active(file):     279336 kB
Inactive(file):   371920 kB
Unevictable:           0 kB
Mlocked:               0 kB
HighTotal:       2493268 kB
HighFree:          52012 kB
LowTotal:         855036 kB
LowFree:          100988 kB
SwapTotal:       4194300 kB
SwapFree:        3128940 kB
Dirty:               160 kB
Writeback:             0 kB
AnonPages:       2113684 kB
Mapped:           128948 kB
Shmem:            187320 kB
Slab:              92736 kB
SReclaimable:      49280 kB
SUnreclaim:        43456 kB
KernelStack:        4408 kB
PageTables:        20956 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:     5868452 kB
Committed_AS:    6277604 kB
VmallocTotal:     122880 kB
VmallocUsed:       26096 kB
VmallocChunk:      48560 kB
HardwareCorrupted:     0 kB
AnonHugePages:     16384 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       4096 kB
DirectMap4k:       20472 kB
DirectMap4M:      884736 kB

```

meminfo is just a text file. There is no man page. How does redhat make meminfo print?

---

### Post by gardnan on 2012-03-16
> **COKEDUDE said:**
> 
```
cat /proc/cpuinfo
cat /proc/meminfo
dmesg
free
top
lspci
sudo dmidecode
cpuid | more
lspci -v | grep VGA
sudo lspci -v -s 00:02.0
sudo lspci -vvv -s 00:02.0
```

Well, I would like to point out a few things. cat /proc/cpuinfo and cat /proc/meminfo aren't new 'commands' per se. cat is just a program that outputs a file, and those particular files happen to be file interfaces to kernel information. In general, it appears like you are copying down whole suggested jobs rather than individual commands, (e.g cpuid | more and lspci -v | grep VGA). Just remember, when you use the '|', you are connecting multiple commands to one another. So, 'grep' and 'more' are just useful everyday commands (well, grep is an everyday useful command :D).

---

