---
title: "gnome pilot sync problems"
date: 2010-08-21
forum: Hardware
---

### Post by kiers on 2010-08-21
HI ALL,
i just installed gnome pilot via the synaptic repositories. i set up the gpilot-applet via gui screens to take USB sync from my Palm Tungsten. it created a new directory called MyPDA. however it is EMPTY, even after syncing. the palm pilot shows sync as ok but nothing seems to be going on really. then i did gpilotd via terminal and got the following errors after pressing the hotsync button again on my palm:

gpilotd-Message: gnome-pilot 2.0.17 starting...
gpilotd-Message: compiled for pilot-link version 0.12.4
gpilotd-Message: compiled with [VFS] [USB] [IrDA] [Network] [Bluetooth] 

(gpilotd:2065): gpilotd-WARNING **: libhal_ctx_init failed: (null)
gpilotd-Message: Activating CORBA server
gpilotd-Message: bonobo_activation_active_server_register = 0
gpilotd-Message: Watching Tungsten (usb:)
gpilotd-Message: Found 4766, 0001
gpilotd-Message: Using net TRUE
gpilotd-Message: Found 0502, 0736
gpilotd-Message: Using net TRUE
gpilotd-Message: Found 091e, 0004
gpilotd-Message: Using net TRUE
gpilotd-Message: Found 115e, f100
gpilotd-Message: Using net TRUE
gpilotd-Message: Found 082d, 0100
gpilotd-Message: Using net FALSE
gpilotd-Message: Found 082d, 0200
gpilotd-Message: Using net TRUE
gpilotd-Message: Found 082d, 0300
gpilotd-Message: Using net TRUE
gpilotd-Message: Found 0c88, 0021
gpilotd-Message: Using net TRUE
gpilotd-Message: Found 0830, 0001
gpilotd-Message: Using net TRUE
gpilotd-Message: Found 0830, 0002
gpilotd-Message: Using net TRUE
gpilotd-Message: Found 0830, 0003
gpilotd-Message: Using net TRUE
gpilotd-Message: Found 0830, 0020
gpilotd-Message: Using net TRUE
gpilotd-Message: Found 0830, 0031
gpilotd-Message: Using net TRUE
gpilotd-Message: Found 0830, 0040
gpilotd-Message: Using net TRUE
gpilotd-Message: Found 0830, 0050
gpilotd-Message: Using net TRUE
gpilotd-Message: Found 0830, 0060
gpilotd-Message: Using net TRUE
gpilotd-Message: Found 0830, 0061
gpilotd-Message: Using net TRUE
gpilotd-Message: Found 0830, 0070
gpilotd-Message: Using net TRUE
gpilotd-Message: Found 0830, 0080
gpilotd-Message: Using net TRUE
gpilotd-Message: Found 04e8, 8001
gpilotd-Message: Using net TRUE
gpilotd-Message: Found 04e8, 6601
gpilotd-Message: Using net TRUE
gpilotd-Message: Found 054c, 0038
gpilotd-Message: Using net TRUE
gpilotd-Message: Found 054c, 0066
gpilotd-Message: Using net TRUE
gpilotd-Message: Found 054c, 0095
gpilotd-Message: Using net TRUE
gpilotd-Message: Found 054c, 009a
gpilotd-Message: Using net TRUE
gpilotd-Message: Found 054c, 00c9
gpilotd-Message: Using net TRUE
gpilotd-Message: Found 054c, 00da
gpilotd-Message: Using net TRUE
gpilotd-Message: Found 054c, 00e9
gpilotd-Message: Using net TRUE
gpilotd-Message: Found 054c, 0144
gpilotd-Message: Using net TRUE
gpilotd-Message: Found 054c, 0169
gpilotd-Message: Using net TRUE
gpilotd-Message: Found 12ef, 0100
gpilotd-Message: Using net TRUE
gpilotd-Message: setting PILOTRATE=57600
gpilotd-Message: Device Tungsten has 0 events
gpilotd-Message: Instantiating 0 conduits...
gpilotd-Message: Instantiated 0 backup conduits, 0 file conduits, 0 other conduits
gpilotd-Message: HotSync button pressed, synchronizing PDA
gpilotd-Message: PDA ID is 19700, name is PalmTungsten, owner is kalm
gpilotd-Message: Pilot has 0 entries in restore queue
gpilotd-Message: Pilot has 0 entries in conduit queue
gpilotd-Message: Synchronization ended
gpilotd-Message: setting PILOTRATE=57600

(gpilotd:2065): gpilotd-WARNING **: An error occurred while getting the PDA's system data

(gpilotd:2065): gpilotd-WARNING **: error -201 from pi_close.
------------------------
what is going wrong?

---

