---
title: "struggling w script to cool CPUs"
date: 2016-05-29
forum: Hardware
---

### Post by watchpocket on 2016-05-29
I've installed the script at [http://seperohacker.blogspot.com/2012/10/linux-keep-your-cpu-cool-with-frequency.html](http://seperohacker.blogspot.com/2012/10/linux-keep-your-cpu-cool-with-frequency.html) (copied below) and badly need to get it working.

***(1)***   I get no errors on startup:

```
--> sudo /home/jr/bin/temp_throttle-master.sh 80  
[sudo] password for jr: 
Author: Sepero 2013 (sepero 111 @ gmx . com)
URL: http://github.com/Sepero/temp-throttle/

Number of CPU cores detected: 4 
```                                                                                                                                                                                                        
                                                                                                                                                                                                                 
***(2)***   I've identified my system temperature-read locations and replaced the "possible locations" list in the script with them:                                         
                                                                                                                                                                                                                 
```
TEMPERATURE_FILES="                                                                                                                                                                                              
/sys/devices/platform/coretemp.0/temp3_input                                                                                                                                                                     
/sys/devices/platform/coretemp.0/temp4_input                                                                                                                                                                     
/sys/devices/platform/coretemp.0/temp5_input                                                                                                                                                                     
                                                                                                                                                                                                                 
null                                                                                                                                                                                                             
"    
```                                                                                                                                                                                                            
                                                                                                                                                                                                                 
But I still get tons of ***"Core temperature above threshold, cpu clock throttled"*** warnings in syslog and dmesg. 

***(3)***   If I include the line:                                                                                                                                                                                     
                                                                                                                                                                                                                 
*/sys/devices/platform/coretemp.0/**temp2**_input                                                                                                                                                                     *
                                                                                                                                                                                                                 
I do get an error message:                                                                                                                                                                                       
                                                                                                                                                                                                                 
```
cat: /sys/devices/platform/coretemp.0/temp2_input: Resource temporarily unavailable                      
/home/jr/bin/temp_throttle-master.sh: line 159: [: -gt: unary operator expected                     
/home/jr/bin/temp_throttle-master.sh: line 161: [: -le: unary operator expected 
```                     
                                                                                                                                                                                                                 
                                                                                                                                                                                                                 
                                                                                                                                                                                                                 
***(4)*** I see at the top of the script:                                                                                                                                                                              
                                                                                                                                                                                                                 
*#!/bin/bash*                                                                                                                                                                                                      
                                                                                                                                                                                                                 
and I'm running zsh.  Do I need to change that line?                                                                                                                                                             
                                                                                                                                                                                                                 
What else might I need to do to get the script functioning correctly? I'd like to at least be able to use it while I track down the source of the over-heating. Thanks.

(Here is the script)
```
 1 #!/bin/bash
  2 
  3 # Usage: temp_throttle.sh max_temp
  4 # USE CELSIUS TEMPERATURES.
  5 # version 2.20
  6 
  7 cat << EOF
  8 Author: Sepero 2013 (sepero 111 @ gmx . com)
  9 URL: http://github.com/Sepero/temp-throttle/
 10 
 11 EOF
 12 
 13 # Additional Links
 14 # http://seperohacker.blogspot.com/2012/10/linux-keep-your-cpu-cool-with-frequency.html
 15 
 16 # Additional Credits
 17 # Wolfgang Ocker <weo AT weo1 DOT de> - Patch for unspecified cpu frequencies.
 18 
 19 # License: GNU GPL 2.0
 20 
 21 # Generic  function for printing an error and exiting.
 22 err_exit () {
 23 *.......echo ""
 24 *.......echo "Error: $@" 1>&2
 25 *.......exit 128
 26 }
 27 
 28 if [ $# -ne 1 ]; then
 29 *.......# If temperature wasn't given, then print a message and exit.
 30 *.......echo "Please supply a maximum desired temperature in Celsius." 1>&2
 31 *.......echo "For example:  ${0} 60" 1>&2
 32 *.......exit 2
 33 else
 34 *.......#Set the first argument as the maximum desired temperature.
 35 *.......MAX_TEMP=$1
 36 fi
 37 
 38 
 39 ### START Initialize Global variables.
 40 
 41 # The frequency will increase when low temperature is reached.
 42 LOW_TEMP=$((MAX_TEMP - 5))
 43 
 44 CORES=$(nproc) # Get number of CPU cores.
 45 echo -e "Number of CPU cores detected: $CORES\n"
 46 CORES=$((CORES - 1)) # Subtract 1 from $CORES for easier counting later.
 47 
 48 # Temperatures internally are calculated to the thousandth.
 49 MAX_TEMP=${MAX_TEMP}000
 50 LOW_TEMP=${LOW_TEMP}000
 51 
 52 FREQ_FILE="/sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies"
 53 FREQ_MIN="/sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_min_freq"
 54 FREQ_MAX="/sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_max_freq"
 55 
 56 # Store available cpu frequencies in a space separated string FREQ_LIST.
 57 if [ -f $FREQ_FILE ]; then
 58 *.......# If $FREQ_FILE exists, get frequencies from it.
 59 *.......FREQ_LIST=$(cat $FREQ_FILE) || err_exit "Could not read available cpu frequencies from file $FREQ_FILE"
 60 elif [ -f $FREQ_MIN -a -f $FREQ_MAX ]; then
 61 *.......# Else if $FREQ_MIN and $FREQ_MAX exist, generate a list of frequencies between them.
 62 *.......FREQ_LIST=$(seq $(cat $FREQ_MAX) -100000 $(cat $FREQ_MIN)) || err_exit "Could not compute available cpu frequencies"
 63 else
 64 *.......err_exit "Could not determine available cpu frequencies"
 65 fi
 66 
 67 FREQ_LIST_LEN=$(echo $FREQ_LIST | wc -w)
 68 
 69 # CURRENT_FREQ will save the index of the currently used frequency in FREQ_LIST.
 70 CURRENT_FREQ=2
 71 
 72 # This is a list of possible locations to read the current system temperature.
 73 TEMPERATURE_FILES="
 74 /sys/devices/platform/coretemp.0/temp3_input
 75 /sys/devices/platform/coretemp.0/temp4_input
 76 /sys/devices/platform/coretemp.0/temp5_input
 77 
 78 null
 79 "
 80 
 81 # /sys/class/thermal/cooling_device0
 82 # /sys/class/thermal/cooling_device1
 83 # /sys/class/thermal/cooling_device2
 84 # /sys/class/thermal/cooling_device3
 85 # /sys/class/thermal/thermal_zone0/temp
 86 # /sys/class/thermal/thermal_zone1/temp
 87 # /sys/class/thermal/thermal_zone2/temp
 88 # /sys/class/hwmon/hwmon0/temp1_input
 89 # /sys/class/hwmon/hwmon1/temp1_input
 90 # /sys/class/hwmon/hwmon2/temp1_input
 91 # /sys/class/hwmon/hwmon0/device/temp1_input
 92 # /sys/class/hwmon/hwmon1/device/temp1_input
 93 # /sys/class/hwmon/hwmon2/device/temp1_input
 94 
 95 # null
 96 # "
 97 
 98 # Store the first temperature location that exists in the variable TEMP_FILE.
 99 # The location stored in $TEMP_FILE will be used for temperature readings.
100 for file in $TEMPERATURE_FILES; do
101 *.......TEMP_FILE=$file
102 *.......[ -f $TEMP_FILE ] && break
103 done
104 
105 [ $TEMP_FILE == "null" ] && err_exit "The location for temperature reading was not found."
106 
107 
108 ### END Initialize Global variables.
109 
110 
111 ### START define script functions.
112 
113 # Set the maximum frequency for all cpu cores.
114 set_freq () {
115 *.......# From the string FREQ_LIST, we choose the item at index CURRENT_FREQ.
116 *.......FREQ_TO_SET=$(echo $FREQ_LIST | cut -d " " -f $CURRENT_FREQ)
117 *.......echo $FREQ_TO_SET
118 *.......for i in $(seq 0 $CORES); do
119 *.......*.......# Try to set core frequency by writing to /sys/devices.
120 *.......*.......{ echo $FREQ_TO_SET 2> /dev/null > /sys/devices/system/cpu/cpu$i/cpufreq/scaling_max_freq; } ||
121 *.......*.......# Else, try to set core frequency using command cpufreq-set.
122 *.......*.......{ cpufreq-set -c $i --max $FREQ_TO_SET > /dev/null; } ||
123 *.......*.......# Else, return error message.
124 *.......*.......{ err_exit "Failed to set frequency CPU core$i. Run script as Root user. Some systems may require to install the package cpufrequtils."; }
125 *.......done
126 }
127 
128 # Will reduce the frequency of cpus if possible.
129 throttle () {
130 *.......if [ $CURRENT_FREQ -lt $FREQ_LIST_LEN ]; then
131 *.......*.......CURRENT_FREQ=$((CURRENT_FREQ + 1))
132 *.......*.......echo -n "throttle "
133 *.......*.......set_freq $CURRENT_FREQ
134 *.......fi
135 }
136 
137 # Will increase the frequency of cpus if possible.
138 unthrottle () {
139 *.......if [ $CURRENT_FREQ -ne 1 ]; then
140 *.......*.......CURRENT_FREQ=$((CURRENT_FREQ - 1))
141 *.......*.......echo -n "unthrottle "
142 *.......*.......set_freq $CURRENT_FREQ
143 *.......fi
144 }
145 
146 get_temp () {
147 *.......# Get the system temperature.
148 *.......
149 *.......TEMP=$(cat $TEMP_FILE)
150 }
151 
152 ### END define script functions.
153 
154 
155 # Mainloop
156 while true; do
157 *.......get_temp # Gets the current tempurature and set it to the variable TEMP.
158 *.......if   [ $TEMP -gt $MAX_TEMP ]; then # Throttle if too hot.
159 *.......*.......throttle
160 *.......elif [ $TEMP -le $LOW_TEMP ]; then # Unthrottle if cool.
161 *.......*.......unthrottle
162 *.......fi
163 *.......sleep 3 # The amount of time between checking tempuratures.
164 done 
```

---

### Post by Yellow Pasque on 2016-05-30
> But I still get tons of "Core temperature above threshold, cpu clock throttled" warnings in syslog and dmesg.

Trying to control overheating with a throttling script seems like trying to cut a tree down by hacking a branch off. Maybe give more detail about the system that's overheating and you can get a better solution.

> 4) I see at the top of the script:
#!/bin/bash
and I'm running zsh. Do I need to change that line? 

I'm not a shell scripting expert, but if it has bash-specific syntax, can't you try it using bash instead of zsh? Or at least use zsh emulation of bash?

---

### Post by watchpocket on 2016-06-04
> *Trying to control overheating with a throttling script seems like trying to cut a tree down by hacking a branch off.*

I kind of thought so too but I was desperate.  It turns out I don't need to use that script -- I've found the source of the overheating problem and fixed it.  The source of the problem was a damaged PCIe slot that the graphics card was plugged into.  I had it replaced, and all appears well, and there are no more overheating warnings.

---

