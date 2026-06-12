---
title: "Small helper script to aid in applying load_cycle_count fix"
date: 2009-01-12
forum: Hardware
---

### Post by seemanta on 2009-01-12
Hi,

I just applied the load cycle count fix over my laptop with Intrepid. Before you read this script, please make sure you read [this thread]("http://ubuntuforums.org/showthread.php?p=5031046") first.

Basically values for hdparm are different from laptop to laptop. You need to apply 254(AC) or 200(Battery) and then monitor the HD temperature. This is where my script comes in handy. Well you could use hddtemp, but I read somewhere that using hddtemp itself causes unnecessary hard disk activity. Hence this script.

So here it goes(As usual, the usual blurb of no warranty and washing my hands off any mishap with your laptop applies with this script ;-) ):


```
#!/bin/bash

# usage " sudo ./HDmon.sh <time_to_refresh>
# where time_to_refresh is an integer which tells after how many seconds
# the SMART readings should be refreshed.

# Store the sleep time parameter for later use
sleep_time=$1
# Run this script in a small xterm window, and as always on top to monitor the
# average Load_Cycle_count and the HDD temperature. The script will also dump
# the values into a file called hdmon_data. 

# Important!! The data is always appended to the hdmon_data file, so delete it
# if you want to take readings from the beginning.


# touch the file, if it does not exist
touch hdmon_data

# Create a marker to denote new stream of data using '****'s
echo "*****************************" >> hdmon_data
# Create the header in the file
echo "Time      Power_on_time     Load_Cycle_Count  Temperature(Deg C)" >> hdmon_data
echo >> hdmon_data

# Now start the indefinite loop to start querying the values using smartctl
while [ true ]
do
# Get the values
set `smartctl -a /dev/sda | egrep '(Temperature|Load_Cycle_Count|Power_On_Hours)'`
# This will store them into  $1, $2 and $3.
set `echo  $@ | cut -d\  -f10,20,30`  

# Dump into the file one by one
echo -n `date | cut -d\   -f4`'     ' >> hdmon_data ; echo "$1              $2             $3" >> hdmon_data

# Show the value in the small xterm window
echo -n "Power on hours -->  " 
echo $1

echo -n "Load cycle count --> "
echo $2

echo -n "Temp   --->  " 
echo $3
echo -n "Avg. Load Cycles/hour ---> " 
# Bash does not have floating point support built-in, so use bc to calculate
# the avg no. of load cycles per hour.
echo "scale=2; $2/$1" | bc

# Sleep for the specified number of seconds before beginning again
sleep $sleep_time
clear
done
```

I have used enough comments to make things clear. However if you need any clarifications, please let me know.

I suggest the following way to use this script:
Open a xterm window, resize it so that it is small enough. Then drag it to a corner of your screen and make it 'Always on Top'. That way you can keep an eye on it as you work.

When you want to end the script, just press 'Ctrl-C' in the xterm window. A file 'hdmon_data' would be created which then you can open in any editor to analyze the Load_Cycle_Count and Temperature of your HDD. So this script will help you to decide your hdparm values before you make them permanent. And remember, this script will always append to the end of the existing hdmon_data and will NEVER delete it.

Also attached screenshot of my desktop which demonstrates how I used this script. Hope this helps. 

regards,
Seemanta

---

### Post by cprofitt on 2009-01-15
Any chance of a fix being put in for 8.10 or 9.04 so we will not need a work-around

---

