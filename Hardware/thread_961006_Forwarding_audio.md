---
title: "Forwarding audio"
date: 2008-10-27
forum: Hardware
---

### Post by binaryloc on 2008-10-27
I need to forward audio output from one computer to another over LAN/WAN.  Note: I must actually send the audio output.  In essence, I want to do something like this:
UBUNTUSERVER~$ cat /dev/audio | nc -l -p 123
UBUNTULAPTOP~$ nc <ip of UBUNTUSERVER> 123 | /dev/audio

except, you know, have it work.

Does anyone have any suggestions?

---

### Post by jocko on 2008-10-28
That's not very difficult, assuming you use pulseaudio as default sound output in all applications on both computers:

1. **Both computers:** Make sure you have the package padevchooser installed:
```
sudo apt-get install padevchooser
```2. **Both computers: **Start padevchoser (Program --> Audio and video --> Pulseaudio device chooser)
This will give you an applet in the system tray. Click the padevchooser applet, select "Preferences", and activate the option "start applet on session login".
3. **Server:** Click the padevchooser applet, choose "Configure local sound server". Activate the options "Enable network access to local sound devices" and "allow other machines on the LAN to discover local sound devices". Log off and log in again to restart pulseaudio.
4. **Laptop:** Copy the file .pulse-cookie (hidden file in the home directory, click ctrl+h to show it) from the server's home directory to your laptop's home directory (allow it to overwrite the file if it already exists. It's important that the file is identical on both computers). Log off and log in again to restart pulseaudio. Click the padevchooser applet, and in the sub menu under "Default sink", you should see an option to use the sound card on your server computer.

Now every new sound application you start on your laptop should forward the sound to your server.

---

