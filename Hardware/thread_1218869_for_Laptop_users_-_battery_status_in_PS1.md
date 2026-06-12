---
title: "for Laptop users - battery status in PS1"
date: 2009-07-21
forum: Hardware
---

### Post by bacil on 2009-07-21
Hi,

i find this really useful, i am runing several laptops with ubuntu and using this on all of them.

Just add following code to your ~/.bashrc and it should work it require acpi package

```

# Battery status for bashrc 
# Orginaly produced by Fabio 'farnis' in 2003
# Modified by Bacil in 2009 
# Main modifications: 1. use of acpi comands instead of /proc/acpi/batter/BAT1/*
#                     2. PS1 to to cope with extra colors
#                     3. color logic
# released under GPL3

BAT_INFO="/proc/acpi/battery/BAT1/info"
BAT_STATE="/proc/acpi/battery/BAT1/state"
AC_STATE="/proc/acpi/ac_adapter/ACAD/state"

function acpi_percent {
  if [ `cat $BAT_STATE | grep present: |cut -f18 -d\ ` = "yes" ]; then
  
   CAPACITY=`acpi -V | grep capacity | awk '{print $10}'`
   LEVEL=`cat $BAT_STATE | grep remaining |cut -f8 -d\ `
   RATE=`cat $BAT_STATE | grep rate | cut -f14 -d\ `
   ACPI_PERCENT=`acpi | awk '{print $4}' | sed 's/,//g'`
   BAT_REMAINING=`acpi | awk '{print $5}'`
   if [ "$LEVEL" -eq "$CAPACITY" ]; then
    echo FULL
   else
    echo $ACPI_PERCENT $BAT_REMAINING
   fi
  }
 else echo "NO BATTERY"
 fi
}

function acpi_charge {
 ACPI_CHARGE=`cat $AC_STATE | cut -f20 -d\ `
 case $ACPI_CHARGE in
       *on-line*)
         ACPI_CHARGE="+" ;;
       *off-line*)
         ACPI_CHARGE="-" ;;
     esac
     echo $ACPI_CHARGE
}

function acpi_color {
     if  [  "$(acpi_charge)"  =  "+"  ];  then
      {
       if [ `cat $BAT_STATE | grep present: |cut -f18 -d\ ` = "no" ]; then
        echo  "0;31"
       else echo  "1;32"
      fi
     }
     else
       case  $(acpi_percent)  in
          10?%)  echo  "0;32"  ;;
           9?%)  echo  "0;32"  ;;
           8?%)  echo  "0;32"  ;;
           7?%)  echo  "0;32"  ;;
           6?%)  echo  "0;32"  ;;
           5?%)  echo  "0;32"  ;;
           4?%)  echo  "0;33"  ;;
           3?%)  echo  "0;33"  ;;
           2?%)  echo  "0;33"  ;;
           1?%)  echo  "0;31"  ;;
            ?%)  echo  "0;31;5"  ;;
             *)  echo  "0;35"  ;;
       esac
     fi
   }
function  acpi_color_prompt {
    PS1='\e[$(acpi_color)m\][$(acpi_charge)$(acpi_percent)]\e[m-\u@\h:\w\$ '
  echo -ne "\033]0;${USER}@${HOSTNAME%%.*}:${PWD/$HOME/~}\007"
}

   #  linux  console
   if  [  "$TERM"  =  "linux"  ];  then
     PROMPT_COMMAND=acpi_color_prompt
   fi
case ${TERM} in
        xterm*|rxvt*|Eterm|aterm|kterm|gnome)
                PROMPT_COMMAND=acpi_color_prompt
esac


function  echo_acpi
   {
     echo -n "($(acpi_charge)$(acpi_percent)) "
   }

```it will produce something like this in your prompt

```
 [-87% 01:40:56]-bacil@one:~$ 
```displaying in different colors based on if we charging or discharging and time either remining n battery or time untill fully charged.

Let me know :-)

---

