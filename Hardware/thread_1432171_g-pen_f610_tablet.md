---
title: "g-pen f610 tablet"
date: 2010-03-17
forum: Hardware
---

### Post by mimoza on 2010-03-17
I've got a Genius tablet G-pen F610 and I have some problems with installation.

I'm follow the steps from here: [https://help.ubuntu.com/community/TabletSetupWizardpen](https://help.ubuntu.com/community/TabletSetupWizardpen) and I'm stuck with this code:

```
<?xml version="1.0" encoding="ISO-8859-1" ?>
            <deviceinfo version="0.2">
            <device>
                <!-- This MUST match with the name of your tablet obtained -->
                <!-- in Step 2 specified previously                        -->
                <match key="info.product" contains="NAME OF YOUR TABLET">
                <merge key="input.x11_driver" type="string">wizardpen</merge>
                <merge key="input.x11_options.SendCoreEvents" type="string">true</merge>

                <!-- Modify these configuration accordingly -->
                <!-- See CONFIGURATION OPTIONS section for the full-set of -->
                <!-- configurable options                                  -->
                <merge key="input.x11_options.TopX" type="string">5619</merge>
                <merge key="input.x11_options.TopY" type="string">6554</merge>
                <merge key="input.x11_options.BottomX" type="string">29405</merge>
                <merge key="input.x11_options.BottomY" type="string">29671</merge>
                <merge key="input.x11_options.MaxX" type="string">29405</merge>
                <merge key="input.x11_options.MaxY" type="string">29671</merge>
                </match>
            </device>
            </deviceinfo>
```

I'm not so skilled with the terminal and I don't know what to write in for the topX, topY, bottomX, bottomY, maxX and maxY.
I guess name of my tablet is just G-pen, or should I write in the whole name?

Thanks in advance :)

---

### Post by tudor117 on 2010-03-21
You should be using the wacom drivers. They're better for the wizard pen as it's a waltop tablet.
See [this post]("http://ubuntuforums.org/showpost.php?p=8676926&postcount=120").
It would be best if you read what was happening. [Here's]("http://ubuntuforums.org/showthread.php?t=1261407&page=12") the specific page.

---

