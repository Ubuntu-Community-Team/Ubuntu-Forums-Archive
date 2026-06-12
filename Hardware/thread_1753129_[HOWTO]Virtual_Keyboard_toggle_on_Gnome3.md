---
title: "[HOWTO]Virtual Keyboard toggle on Gnome3"
date: 2011-05-08
forum: Hardware
---

### Post by wansors on 2011-05-08
Hi,
I have a Tablet running 11.04 with gnome3. One of the biggest problems is the lack of a good virtual keyboard. Until some projects like maliit are integrated inside the system, I've made a small script to temporally solve the problem. I want to share here a way to toggle the keyboard using an application or touching the gnome3 panel.


Bash script to toggle the virtual keyboard (I'm using matchbox-keyboard) located at /usr/bin/toggle_keyboard.sh 
```

#!/bin/bash
#This script toggle the virtual keyboard

PID=`pidof matchbox-keyboard`
if [ ! -e $PID ]; then
  killall matchbox-keyboard
else
 matchbox-keyboard&
fi

```It's recommended to create a .desktop file to access from the apps menu (Maybe it will work also with unity)
/usr/share/applications/toggle_keyboard.desktop
```

[Desktop Entry]
Name=Toggle keyboard
Comment=Activate/Deactivate keyboard
Exec=toggle_keyboard.sh
Icon=keyboard
Terminal=false
Type=Application
StartupNotify=false

```You can toggle your keyboard using the app, but following some tutorials [http://blog.fpmurphy.com/2011/04/gnome-3-shell-extensions.html](http://blog.fpmurphy.com/2011/04/gnome-3-shell-extensions.html) I've created a gnome-shell extension to toggle the keyboard when you click (or touch) the gnome3 panel.

To create the extension just follow this steps:

[LIST=1]
[*]gnome-shell-extension-tool  --create-extension
[*]Name: Toggle Keyboard
[*]Description: Open and close the matchbox-keyboard
[*]#Add a cool name to your extension ;)
[*]Replace the code in extension.js with:
[/LIST]
```

// Sample extension code, makes clicking on the panel show a message
const St = imports.gi.St;
const Mainloop = imports.mainloop;
const Shell = imports.gi.Shell;
const Main = imports.ui.main;

function _showHello() {
    let text = new St.Label({ style_class: 'helloworld-label', text: "Keyboard" });
    let monitor = global.get_primary_monitor();
    global.stage.add_actor(text);
    text.set_position(Math.floor (monitor.width / 2 - text.width / 2), Math.floor(monitor.height / 2 - text.height / 2));
    Mainloop.timeout_add(1000, function () { text.destroy(); });
    let app = Shell.AppSystem.get_default().get_app('toggle_keyboard.desktop');
    app.activate(-1);
}

// Put your extension initialization code here
function main() {
    Main.panel.actor.reactive = true;
    Main.panel.actor.connect('button-release-event', _showHello);
}

```Now restart your desktop and touch the panel to toggle matchbox-keyboard.

This is not the coolest way to integrate the virtual keyboard on gnome but for me it's enough

---

### Post by fulanodetal316 on 2011-10-17
Gnome Shell changed their API a bit. Took forever to track down the new commands.

Does anyone know where they publish their API? I only found this through someone's comment on a github commit that showed up on google.

Bah.

Anyhow, this code will probably work (As of Oct 17, w/ 11.10).

BTW: I used Alacarte to generate the desktop file, hence the name.
```

const Shell = imports.gi.Shell;
const St = imports.gi.St;
const Main = imports.ui.main;

let button;

function _toggleKeyBoard() {
	let app = Shell.AppSystem.get_default().lookup_app('alacarte-made-2.desktop');
	app.activate(-1);
}	

function init() {
    button = new St.Bin({ style_class: 'panel-button',
                          reactive: true,
                          can_focus: true,
                          x_fill: true,
                          y_fill: false,
                          track_hover: true });
    let icon = new St.Icon({ icon_name: 'system-run',
                             icon_type: St.IconType.SYMBOLIC,
                             style_class: 'system-status-icon' });

    button.set_child(icon);
    button.connect('button-press-event', _toggleKeyBoard);
}

function enable() {
    Main.panel._rightBox.insert_actor(button, 0);
}

function disable() {
    Main.panel._rightBox.remove_actor(button);
}
```

---

