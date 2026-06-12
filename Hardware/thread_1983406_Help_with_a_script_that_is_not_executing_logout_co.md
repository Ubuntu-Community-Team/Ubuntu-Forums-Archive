---
title: "Help with a script that is not executing logout command."
date: 2012-05-20
forum: Hardware
---

### Post by vedovatti on 2012-05-20
Hi there, I am trying to make work a script for switchable (hybrid) graphics with vgaswitcheroo. So far it works, but it does not execute the logout command.

The script is this one:
[PHP]#!/bin/bash
# "switch_between_cards.sh" script by RM, with useful changes from LoLL
# version 20101107

pci_integrated=$(lspci | grep VGA | sed -n '1p' | cut -f 1 -d " ")
pci_discrete=$(lspci | grep VGA | sed -n '2p' | cut -f 1 -d " ")

integrated=$(cat /sys/kernel/debug/vgaswitcheroo/switch | grep $pci_integrated | grep -o -P ':.:...:')
discrete=$(cat /sys/kernel/debug/vgaswitcheroo/switch | grep $pci_discrete | grep -o -P ':.:...:')

name_integrated=$(lspci | grep VGA | sed -n '1p' | sed -e "s/.* VGA compatible controller[ :]*//g" | sed -e "s/ Corporation//g" | sed -e "s/ Technologies Inc//g" | sed -e 's/\[[0-9]*\]: //g' | sed -e 's/\[[0-9:a-z]*\]//g' | sed -e 's/(rev [a-z0-9]*)//g' | sed -e "s/ Integrated Graphics Controller//g")

name_discrete=$(lspci | grep VGA | sed -n '2p' | sed -e "s/.* VGA compatible controller[ :]*//g" | sed -e "s/ Corporation//g" | sed -e "s/ Technologies Inc//g" | sed -e 's/\[[0-9]*\]: //g' | sed -e 's/\[[0-9:a-z]*\]//g' | sed -e 's/(rev [a-z0-9]*)//g' | sed -e "s/ Integrated Graphics Controller//g")

if [ "$integrated" = ":+:Pwr:" ]
then
 integrated_condition="(*) - Power ON"
elif [ "$integrated" = ": :Pwr:" ]
then
 integrated_condition="( ) - Power ON"
elif [ "$integrated" = ": :Off:" ]
then
 integrated_condition="( ) - Power OFF"
fi

if [ "$discrete" = ":+:Pwr:" ]
then
 discrete_condition="(*) - Power ON"
elif [ "$discrete" = ": :Pwr:" ]
then
 discrete_condition="( ) - Power ON"
elif [ "$discrete" = ": :Off:" ]
then
 discrete_condition="( ) - Power OFF"
fi

gxmessage -center \
          -buttons "_Cancel":1,"switch to _Integrated":101,"switch to _Discrete":102 \
          -wrap \
          -title "Choose Hybrid Graphic Card" \
"Choose Hybrid Graphic Card
=================
Integrated: $integrated_condition : $name_integrated
Discrete: $discrete_condition : $name_discrete"


whichCard=$?

case "$whichCard" in

1)
 echo "Exit"
;;
101)
 if [ "$integrated" == ":+:Pwr:" ] && [ "$discrete" == ": :Pwr:" ]
 then
  notify-send -t 5000 --icon="/usr/share/icons/hardware_down.png" "switching to $name_integrated"
  echo OFF > /sys/kernel/debug/vgaswitcheroo/switch
 elif [ "$integrated" == ": :Pwr:" ] && [ "$discrete" == ":+:Pwr:" ]
 then
  notify-send -t 5000 --icon="/usr/share/icons/hardware_down.png" "switching to $name_integrated"
  echo DIGD > /sys/kernel/debug/vgaswitcheroo/switch
  if [ "$DESKTOP_SESSION" = "openbox" ]
  then
  gnome-session-quit
  elif [ "$DESKTOP_SESSION" = "gnome" ]
  then
  gnome-session-quit
  fi
 elif [ "$integrated" == ": :Off:" ] && [ "$discrete" == ":+:Pwr:" ]
 then
  notify-send -t 5000 --icon="/usr/share/icons/hardware_down.png" "switching to $name_integrated"
  echo ON > /sys/kernel/debug/vgaswitcheroo/switch
  echo DIGD > /sys/kernel/debug/vgaswitcheroo/switch
  if [ "$DESKTOP_SESSION" = "openbox" ]
  then
  gnome-session-quit
  elif [ "$DESKTOP_SESSION" = "gnome" ]
  then
  gnome-session-quit
  fi
 elif [ "$integrated" == ":+:Pwr:" ] && [ "$discrete" == ": :Off:" ]
 then
  notify-send -t 5000 --icon="/usr/share/icons/hardware_down.png" "already switched to $name_integrated"  
 fi
;;
102)
 if [ "$integrated" == ":+:Pwr:" ] && [ "$discrete" == ": :Pwr:" ]
 then
  notify-send -t 5000 --icon="/usr/share/icons/hardware_up.png" "switching to $name_discrete"
  echo DDIS > /sys/kernel/debug/vgaswitcheroo/switch
  if [ "$DESKTOP_SESSION" = "openbox" ]
  then
   gnome-session-quit
  elif [ "$DESKTOP_SESSION" = "gnome" ]
  then
  gnome-session-quit
  fi
 elif [ "$integrated" == ": :Pwr:" ] && [ "$discrete" == ":+:Pwr:" ]
 then
  notify-send -t 5000 --icon="/usr/share/icons/hardware_up.png" "switching to $name_discrete"
  echo OFF > /sys/kernel/debug/vgaswitcheroo/switch
 elif [ "$integrated" == ":+:Pwr:" ] && [ "$discrete" == ": :Off:" ]
 then
  notify-send -t 5000 --icon="/usr/share/icons/hardware_up.png" "switching to $name_discrete"  
  echo ON > /sys/kernel/debug/vgaswitcheroo/switch
  echo DDIS > /sys/kernel/debug/vgaswitcheroo/switch
  if [ "$DESKTOP_SESSION" = "openbox" ]
  then
  gnome-session-quit
  elif [ "$DESKTOP_SESSION" = "gnome" ]
  then
  gnome-session-quit
  fi
 elif [ "$integrated" == ": :Off:" ] && [ "$discrete" == ":+:Pwr:" ]
 then
  notify-send -t 5000 --icon="/usr/share/icons/hardware_up.png" "already switched to $name_discrete"  
 fi
;;
esac[/PHP]
after switching switching between cards, it supposed to run "gnome-session-quit", but it doesnt do it.

Any idea?

---

