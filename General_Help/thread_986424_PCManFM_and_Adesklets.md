---
title: "PCManFM and Adesklets"
date: 2008-11-18
forum: General Help
---

### Post by Mark76 on 2008-11-18
Does anyone know if it's possible to get adesklets to sit on top of the PCManFM fake root window?

Or should I just continue using Feh to manage the backdrop?

---

### Post by kerry_s on 2008-11-18
:lolflag: > ROX All The Way!

Yeah baby!!!! 

you to huh. i'm also running pcmanfm instead my usual rox.

i'd use feh.

---

### Post by Mark76 on 2008-11-18
I am a file manager tart :p :lol:

---

### Post by kerry_s on 2008-11-18
> **Mark76 said:**
> I am a file manager tart :p :lol:

it's alright, i was just doing the same thing, i tried every file manager in the repo to see if anything improved. i still remember when pcmanfm would crash like crazy, which is why i continued using rox, but pcmanfm is a heck of a lot better now, i just wish it had the right click> set icon, other than that it's pretty nice. i also don't use the desktop feature, i think they should just dump that, just make it a simple fast file manager and thats all.

this is what it does to me.

---

### Post by Mark76 on 2008-11-18
When I tried it as a backdrop manager I commented out the line in my openbox session autostart file that launched feh. But when I deselected "manage desktop" in PCManFM preferences feh was running underneath it. Complete with adesklets.

I wonder if you need to kill your original default desktop manager first?

---

### Post by kerry_s on 2008-11-18
> **Mark76 said:**
> When I tried it as a backdrop manager I commented out the line in my openbox session autostart file that launched feh. But when I deselected "manage desktop" in PCManFM preferences feh was running underneath it. Complete with adesklets.

I wonder if you need to kill your original default desktop manager first?

that would kill everything, everything is jwm, i don't need to use a extra program to put stuff on the desktop, i do it all with jwm.

what it tells me though is pcman does not use the root desktop, it's just above the root. all the stuff on my desktop is on the root, layer 0.

---

### Post by Mark76 on 2008-11-19
Well, if jwm already manages the desktop background you don't really need another program to do it.

---

### Post by kerry_s on 2008-11-19
> **Mark76 said:**
> Well, if jwm already manages the desktop background you don't really need another program to do it.

exactly. :)
with jwm i manage everything with 1 file, .jwmrc.
i do everything from desktop launchers to swallowing programs into the desktop, backgrounds to, even though i only use solid black, it can do images.

```
 <?xml version="1.0"?>
 
 <JWM>
 
<StartupCommand>
rm -f ~/.serverauth.*
rm -f ~/.xsession-errors
xdkcal
</StartupCommand>

<Group>
<Name>xmessage</Name>
<Option>nolist</Option>
<Option>noborder</Option>
<Option>notitle</Option>
</Group>


    <!-- The root menu, if this is undefined you will not get a menu. -->
    <!-- Additional RootMenu attributes: onroot, labeled, label -->
    <RootMenu height="25" onroot="3">
       <Program label="Terminal">exec xterm -T "Terminal" -fn 9x15</Program>
       <Program label="File Manager">exec pcmanfm</Program>
       <Program label="Web Browser">exec xmessage -fn 10x20 -center -timeout 5 " Starting Web Browser " -buttons , | iceweasel</Program>
    <Separator/>
       <Restart label="Restart JWM"/>
    </RootMenu>


    <RootMenu height="25" onroot="0">
       <Program label="Root File Manager">exec sudo pcmanfm /</Program>
       <Program label="Manage Programs">exec sudo synaptic</Program>
       <Program label="Edit xorg.conf">exec sudo leafpad /etc/X11/xorg.conf</Program>
    </RootMenu>


    <RootMenu height="25" onroot="6">
       <Program label="Edit .jwmrc">exec leafpad ~/.jwmrc</Program>
       <Program label="Edit .scripts">exec pcmanfm ~/.scripts</Program>
       <Program label="Sound settings">exec xterm -fn 9x15 -e alsamixer</Program>
    </RootMenu>


    <RootMenu height="25" onroot="7">
       <Program label="Calculator">exec galculator</Program>
       <Program label="Word">exec abiword</Program>
    </RootMenu>


       <Tray x="10" y="10" layer="0" layout="horizontal">
        <TrayButton label=" Adminstration  ">root:0</TrayButton>
        <TrayButton icon="*.png"/>
        <TrayButton label=" Settings  ">root:6</TrayButton>
        <TrayButton icon="*.png"/>
        <TrayButton label=" Office  ">root:7</TrayButton>
       </Tray>


       <Tray x="-1" y="1" layer="0" width="700">
        <Swallow name="xterm">xterm -fn 9x15</Swallow>
       </Tray>


       <Tray x="-10" y="500" layer="0" layout="vertical">
        <TrayButton label=" Suspend  ">exec: ~/.scripts/suspend</TrayButton>
        <TrayButton icon="*.png"/>
        <TrayButton label="Logout">exec: ~/.scripts/logout</TrayButton>
       </Tray>

 
    <!-- Additional tray attributes: autohide, width, border, layer, layout -->
    <Tray  x="0" y="-1" height="32">
       <!-- Additional TrayButton attribute: label -->
       <TrayButton icon="logo.png" label="JWM  ">root:3</TrayButton>
       <TrayButton label="_">showdesktop</TrayButton>
       <!-- Additional TaskList attribute: maxwidth -->
       <TaskList/>
       <Dock/>
       <Clock format="%l:%M" width="70">exec gtodo</Clock>
    </Tray>


    <Tray  x="0" y="-35" width="128" autohide="true">
       <Pager/>
     </Tray>


    <Tray  x="-1" y="-35" width="60" autohide="true">
        <TrayButton label="up">exec: amixer set PCM 3+ unmute</TrayButton>
        <TrayButton label="down">exec: amixer set PCM 3- unmute</TrayButton>
        <TrayButton label="mute">exec: amixer set PCM toggle</TrayButton>
     </Tray>


    <!-- Visual Styles -->
 
    <WindowStyle>
 
       <Font>mono-9</Font>
       <Width>4</Width>
       <Height>20</Height>
 
       <Active>
          <Text>white</Text>
          <Title>#2e3a67:#303438</Title>
          <Corner>white</Corner>
          <Outline>black</Outline>
       </Active>
 
       <Inactive>
          <Text>#aaaaaa</Text>
          <Title>#808488:#303438</Title>
          <Corner>#aaaaaa</Corner>
          <Outline>black</Outline>
       </Inactive>
 
    </WindowStyle>
 
    <TaskListStyle>
       <Font>sans-12</Font>
       <ActiveForeground>white</ActiveForeground>
       <ActiveBackground>#2e3a67:#303438</ActiveBackground>
       <Foreground>black</Foreground>
       <Background>gray70:gray90</Background>
    </TaskListStyle>
 
    <!-- Additional TrayStyle attribute: insert -->
    <TrayStyle>
       <Font>sans-12</Font>
       <Background>gray90</Background>
       <Foreground>black</Foreground>
    </TrayStyle>
 
    <PagerStyle>
       <Outline>black</Outline>
       <Foreground>gray90</Foreground>
       <Background>#808488</Background>
       <ActiveForeground>#70849d</ActiveForeground>
       <ActiveBackground>#2e3a67</ActiveBackground>
    </PagerStyle>
 
    <MenuStyle>
       <Font>sans-12</Font>
       <Foreground>black</Foreground>
       <Background>gray90</Background>
       <ActiveForeground>white</ActiveForeground>
       <ActiveBackground>#2e3a67:#303438</ActiveBackground>
    </MenuStyle>
 
    <PopupStyle enabled="false"/>
 
    <IconPath>
       $HOME/.icons
    </IconPath>
 
    <!-- Virtual Desktops -->
    <!-- Desktop tags can be contained within Desktops for desktop names. -->
    <Desktops count="3">
 
       <!-- Default background. Note that a Background tag can be
            contained within a Desktop tag to give a specific background
            for that desktop.
        -->
       <Background type="solid">black</Background>
 
    </Desktops>
 
    <!-- Double click speed (in milliseconds) -->
    <DoubleClickSpeed>400</DoubleClickSpeed>
 
    <!-- Double click delta (in pixels) -->
    <DoubleClickDelta>2</DoubleClickDelta>
 
    <!-- The focus model (sloppy or click) -->
    <FocusModel>click</FocusModel>
 
    <!-- The snap mode (none, screen, or border) -->
    <SnapMode distance="10">border</SnapMode>
 
    <!-- The move mode (outline or opaque) -->
    <MoveMode>outline</MoveMode>
 
    <!-- The resize mode (outline or opaque) -->
    <ResizeMode>outline</ResizeMode>
 
    <!-- Key bindings -->
    <Key key="Up">up</Key>
    <Key key="Down">down</Key>
    <Key key="Right">right</Key>
    <Key key="Left">left</Key>
    <Key key="Return">select</Key>
    <Key key="Escape">escape</Key>
 
    <Key mask="A" key="Tab">nextstacked</Key>
    <Key mask="A" key="F4">close</Key>
    <Key mask="A" key="#">desktop#</Key>
    <Key mask="A" key="F1">root:3</Key>
    <Key mask="A" key="F2">exec: grun</Key>
    <Key mask="C" key="Super_L">exec: sleep 1;xset dpms force off</Key>
    <Key mask="" key="Print">exec: scrot %T.png;xmessage -fn 10x20 -center -timeout 1 -buttons , " Screenshot done "</Key>
    <Key mask="A" key="Print">exec: xmessage -fn 10x20 -center -timeout 1 -buttons , " click or click drag to select ";scrot -sb %T.png;xmessage -fn 10x20 -center -timeout 1 -buttons , " Screenshot done "</Key>
    <Key mask="CA" key="Print">exec: xterm -T "Screenshot" -fn 10x20 -g 40x1+350+0 -e scrot -cd 5 %T.png;xmessage -fn 10x20 -center -timeout 1 -buttons , " Screenshot done "</Key>
    <Key mask="C" key="Up">exec: amixer set PCM 3+ unmute</Key>
    <Key mask="C" key="Down">exec: amixer set PCM 3- unmute</Key>
 </JWM>
 
 

```

here's with xterm swallowed on the desktop.

---

