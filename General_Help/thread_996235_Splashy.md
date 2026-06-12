---
title: "Splashy"
date: 2008-11-28
forum: General Help
---

### Post by amiller2571 on 2008-11-28
Hello. I am trying to setup a new Splashy boot screen for my Desktop. I got everything working except the shutdown screen. When ever I shutdown my computer it just going to the text and not the image I set for it.
Here is the code I'm using

[COLOR="Red"]<?xml version="1.0" encoding="UTF-8"?>
<splashy xmlns:xsi="none"
    xsi:schemaLocation="none">
    <info>
        <!-- theme name is case sensitive. use directory name -->
        <name>amiller</name>
        <version>0.1</version>
        <description>Home made</description>
        <urls></urls>
        <author>me</author>
    </info>
    <progressbar>
        <!-- here are tags to set the bar... x coordinate,
        y coordinate, width and height are for the progress bar.
        Remember that x, y, width and height are expressed in percentage -->
        <dimension>
            <x>10</x>
            <y>90</y>
            <width>80</width>
            <height>5</height>
        </dimension>
        <!-- here you can set the color of the progressbar...
        set the amount of red, green, blue and alpha channel. 
        Remember that the max value is 255 and the minumun value is 0-->
        <color>
            <red>152</red>
            <green>1</green>
            <blue>1</blue>
            <alpha>255</alpha>
        </color>
        <!-- whether or not you want a border around the progressbar. default: no -->
        <border>
            <enable>yes</enable>
            <color>
                <red>0</red>
                <green>0</green>
                <blue>0</blue>
                <alpha>255</alpha>
            </color>
        </border>
        <!-- here you can set the color of the progressbar background
        set the amount of red, green, blue and alpha channel. 
        Remember that the max value is 255 and the minumun value is 0-->
        <background>
            <color>
                <red>127</red>
                <green>127</green>
                <blue>127</blue>
                <alpha>255</alpha>
            </color>
        </background>
        <direction>
            <boot>forward</boot>
            <shutdown>backward</shutdown>
            <resume>forward</resume>
            <suspend>backward</suspend>
        </direction>
        <visibility>
            <boot>yes</boot>
            <shutdown>yes</shutdown>
            <resume>yes</resume>
            <suspend>yes</suspend>
        </visibility>
    </progressbar>
    <!-- conventional path: /etc/splashy/themes + theme-name -->
    <background>
        <boot>startup.png</boot>
        <shutdown>shutdown.png</shutdown>
        <resume>startup.png</resume>
        <suspend>shutdown.png</suspend>
        <errorimg>error.png</errorimg>
        <!-- resolution of the images. this value affects where 
        the progressbar will be drawn. If VALUE <= 0, then percentages
        of the screen width and hight will be assumed -->
        <dimension>
            <!-- NOTE: x and y are not used by splashy -->
            <x>0</x>
            <y>0</y>
            <width>0</width>
            <height>0</height>
        </dimension>
    </background>
    <textbox>
        <!-- whether you want the textbox always
        shown or no. If no, it will be shown only on error, 
        see autoverboseonerror -->
        <enable>no</enable>
        <!-- here are tags to set the text area... x coordinate,
        y coordinate, width and height are for the text area.
        Remember that x, y, width and height are expressed in percentage
        or pixel units -->
        <dimension>
            <x>20</x>
            <y>50</y>
            <width>60</width>
            <height>40</height>
        </dimension>
        <!-- here you can set the color of the text area...
        set the amount of red, green, blue and alpha channel. 
        Remember that the max value is 255 and the minumun value is 0-->
        <color>
            <red>0</red>
            <green>0</green>
            <blue>0</blue>
            <alpha>127</alpha>
        </color>
        <!-- whether or not you want a border around the progressbar. default: no -->
        <border>
            <enable>yes</enable>
            <color>
                <red>0</red>
                <green>0</green>
                <blue>0</blue>
                <alpha>255</alpha>
            </color>
        </border>
        <text>
            <!-- font file to use, path relative to theme -->
            <font>
                <file>FreeMono.ttf</file>
                <height>10</height>
            </font>
            <!-- here you can set the color of the text/font...
            set the amount of red, green, blue and alpha channel. 
            Remember that the max value is 255 and the minumun value is 0-->
            <color>
                <red>128</red>
                <green>128</green>
                <blue>32</blue>
                <alpha>255</alpha>
            </color>
        </text>
    </textbox>
    <autoverboseonerror>no</autoverboseonerror>
    <fadein>no</fadein>
    <fadeout>no</fadeout>
</splashy>[/COLOR]

If anyone could help me I would be very greatfull.

---

### Post by amiller2571 on 2008-11-28
I also should say that it shuts down very fast now. before I started this it would take the expected amount of time to shutdown but now I can't even count to 3 before it's done.

and the shutdown image did work once out of the blue, but just that once.

---

