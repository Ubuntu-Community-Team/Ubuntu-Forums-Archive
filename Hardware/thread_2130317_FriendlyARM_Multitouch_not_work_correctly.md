---
title: "FriendlyARM Multitouch not work correctly"
date: 2013-03-29
forum: Hardware
---

### Post by neochapay on 2013-03-29
I have FriendlyARM tiny210v2 devboard whith installed Ubuntu but cataptive touchscteen work like mouse

evtest say:
```

No device specified, trying to scan all of /dev/input/event*
Available devices:
/dev/input/event0:      fa_ts_input
/dev/input/event1:      mma7660
/dev/input/event2:      ft5x0x_ts
Select the device event number [0-2]: 2
Input driver version is 1.0.1
Input device ID: bus 0x18 vendor 0x12fa product 0x2143 version 0x100
Input device name: "ft5x0x_ts"
Supported events:
  Event type 0 (EV_SYN)
  Event type 1 (EV_KEY)
  Event type 3 (EV_ABS)
    Event code 48 (ABS_MT_TOUCH_MAJOR)
      Value      0
      Min        0
      Max      255
    Event code 50 (ABS_MT_WIDTH_MAJOR)
      Value      0
      Min        0
      Max      200
    Event code 53 (ABS_MT_POSITION_X)
      Value      0
      Min        0
      Max      800
    Event code 54 (ABS_MT_POSITION_Y)
      Value      0
      Min        0
      Max      480
    Event code 57 (ABS_MT_TRACKING_ID)
      Value      0
      Min        0
      Max        5
Properties:
Testing ... (interrupt to exit)

```

```

<?xml version="1.0" encoding="ISO-8859-1"?>
<evtest-capture>
    <info>
        <id bus="0x18" vendor="0x12fa" product="0x2143" version="0x100">ft5x0x_ts</id>
        <event-type type="EV_SYN"/>
        <event-type type="EV_KEY"/>
        <event-type type="EV_ABS">
            <code  value="ABS_MT_TOUCH_MAJOR" abs-value="0" abs-min="0" abs-max="255"  abs-fuzz="0" abs-flat="0" abs-resolution="0"/>
            <code  value="ABS_MT_WIDTH_MAJOR" abs-value="0" abs-min="0" abs-max="200"  abs-fuzz="0" abs-flat="0" abs-resolution="0"/>
            <code  value="ABS_MT_POSITION_X" abs-value="0" abs-min="0" abs-max="800"  abs-fuzz="0" abs-flat="0" abs-resolution="0"/>
            <code  value="ABS_MT_POSITION_Y" abs-value="0" abs-min="0" abs-max="480"  abs-fuzz="0" abs-flat="0" abs-resolution="0"/>
            <code  value="ABS_MT_TRACKING_ID" abs-value="0" abs-min="0" abs-max="5"  abs-fuzz="0" abs-flat="0" abs-resolution="0"/>
        </event-type>
    </info>
    <events>
        <event sec="59001" usec="238755" type="EV_ABS" code="ABS_MT_POSITION_X" value="377"/>
        <event sec="59001" usec="238763" type="EV_ABS" code="ABS_MT_POSITION_Y" value="242"/>
        <event sec="59001" usec="238766" type="EV_ABS" code="ABS_MT_TOUCH_MAJOR" value="200"/>
        <event sec="59001" usec="238768" type="EV_ABS" code="ABS_MT_TRACKING_ID" value="0"/>
        <event sec="59001" usec="238769" type="EV_SYN" code="EV_REL" value="0"/>
        <event sec="59001" usec="238770" type="EV_SYN" code="EV_SYN" value="0"/>
        <event sec="59001" usec="261949" type="EV_ABS" code="ABS_MT_POSITION_X" value="377"/>
        <event sec="59001" usec="261952" type="EV_ABS" code="ABS_MT_POSITION_Y" value="242"/>
        <event sec="59001" usec="261954" type="EV_ABS" code="ABS_MT_TOUCH_MAJOR" value="200"/>
        <event sec="59001" usec="261956" type="EV_ABS" code="ABS_MT_TRACKING_ID" value="0"/>
        <event sec="59001" usec="261957" type="EV_SYN" code="EV_REL" value="0"/>
        <event sec="59001" usec="261958" type="EV_SYN" code="EV_SYN" value="0"/>
        <event sec="59001" usec="286978" type="EV_SYN" code="EV_REL" value="0"/>
        <event sec="59001" usec="286981" type="EV_SYN" code="EV_SYN" value="0"/>
        <event sec="59001" usec="947576" type="EV_ABS" code="ABS_MT_POSITION_X" value="213"/>
        <event sec="59001" usec="947579" type="EV_ABS" code="ABS_MT_POSITION_Y" value="224"/>
        <event sec="59001" usec="947581" type="EV_ABS" code="ABS_MT_TOUCH_MAJOR" value="200"/>
        <event sec="59001" usec="947583" type="EV_ABS" code="ABS_MT_TRACKING_ID" value="0"/>
        <event sec="59001" usec="947584" type="EV_SYN" code="EV_REL" value="0"/>
        <event sec="59001" usec="947586" type="EV_ABS" code="ABS_MT_POSITION_X" value="549"/>
        <event sec="59001" usec="947587" type="EV_ABS" code="ABS_MT_POSITION_Y" value="232"/>
        <event sec="59001" usec="947589" type="EV_ABS" code="ABS_MT_TOUCH_MAJOR" value="200"/>
        <event sec="59001" usec="947591" type="EV_ABS" code="ABS_MT_TRACKING_ID" value="1"/>
        <event sec="59001" usec="947593" type="EV_SYN" code="EV_REL" value="0"/>
        <event sec="59001" usec="947594" type="EV_SYN" code="EV_SYN" value="0"/>
        <event sec="59001" usec="970447" type="EV_ABS" code="ABS_MT_POSITION_X" value="213"/>
        <event sec="59001" usec="970450" type="EV_ABS" code="ABS_MT_POSITION_Y" value="224"/>
        <event sec="59001" usec="970452" type="EV_ABS" code="ABS_MT_TOUCH_MAJOR" value="200"/>
        <event sec="59001" usec="970454" type="EV_ABS" code="ABS_MT_TRACKING_ID" value="0"/>
        <event sec="59001" usec="970455" type="EV_SYN" code="EV_REL" value="0"/>
        <event sec="59001" usec="970456" type="EV_ABS" code="ABS_MT_POSITION_X" value="549"/>
        <event sec="59001" usec="970458" type="EV_ABS" code="ABS_MT_POSITION_Y" value="232"/>
        <event sec="59001" usec="970460" type="EV_ABS" code="ABS_MT_TOUCH_MAJOR" value="200"/>
        <event sec="59001" usec="970462" type="EV_ABS" code="ABS_MT_TRACKING_ID" value="1"/>
        <event sec="59001" usec="970463" type="EV_SYN" code="EV_REL" value="0"/>
        <event sec="59001" usec="970464" type="EV_SYN" code="EV_SYN" value="0"/>
        <event sec="59001" usec="994199" type="EV_ABS" code="ABS_MT_POSITION_X" value="213"/>
        <event sec="59001" usec="994202" type="EV_ABS" code="ABS_MT_POSITION_Y" value="224"/>
        <event sec="59001" usec="994204" type="EV_ABS" code="ABS_MT_TOUCH_MAJOR" value="200"/>
        <event sec="59001" usec="994206" type="EV_ABS" code="ABS_MT_TRACKING_ID" value="0"/>
        <event sec="59001" usec="994207" type="EV_SYN" code="EV_REL" value="0"/>
        <event sec="59001" usec="994209" type="EV_ABS" code="ABS_MT_POSITION_X" value="549"/>
        <event sec="59001" usec="994210" type="EV_ABS" code="ABS_MT_POSITION_Y" value="232"/>
        <event sec="59001" usec="994212" type="EV_ABS" code="ABS_MT_TOUCH_MAJOR" value="200"/>
        <event sec="59001" usec="994214" type="EV_ABS" code="ABS_MT_TRACKING_ID" value="1"/>
        <event sec="59001" usec="994215" type="EV_SYN" code="EV_REL" value="0"/>
        <event sec="59001" usec="994216" type="EV_SYN" code="EV_SYN" value="0"/>
        <event sec="59002" usec="17105" type="EV_SYN" code="EV_REL" value="0"/>
        <event sec="59002" usec="17107" type="EV_SYN" code="EV_SYN" value="0"/>
    </events>
</evtest-capture>

```

How can I make it work properly?

---

### Post by neochapay on 2013-03-30
Hm... 59 views and 0 answers....
ok be easier : how to configure multitouch screen on ubuntu ?

---

