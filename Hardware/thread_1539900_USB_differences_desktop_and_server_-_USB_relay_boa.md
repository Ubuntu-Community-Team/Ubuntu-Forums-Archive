---
title: "USB differences desktop and server? - USB relay board LRB"
date: 2010-07-27
forum: Hardware
---

### Post by hbar86 on 2010-07-27
Hi

I have a problem with my USB relay board LRP from [www.Abacom-online.de]("http://www.Abacom-online.de") on my Ubuntu 10.04 server. 

The following program is used to control it on linux systems:


/*  usb-relay - a tiny control program for a CH341A based relay board.
    Copyright (C) 2010  Henning Rohlfs

    This program is free software: you can redistribute it and/or modify
    it under the terms of the GNU General Public License as published by
    the Free Software Foundation, either version 3 of the License, or
    (at your option) any later version.

    This program is distributed in the hope that it will be useful,
    but WITHOUT ANY WARRANTY; without even the implied warranty of
    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
    GNU General Public License for more details.

    You should have received a copy of the GNU General Public License
    along with this program.  If not, see <http://www.gnu.org/licenses/>. */


#include <stdio.h>
#include <usb.h>
#include <iostream>
#include <fstream>
#include <set>
using namespace std;


static struct usb_device *findRelay(uint16_t vendor, uint16_t product)
{
    usb_init();
    usb_find_busses();
    usb_find_devices();
    struct usb_bus *busses = usb_get_busses();

    for (struct usb_bus *bus = busses; bus; bus = bus->next) {
        for (struct usb_device *dev = bus->devices; dev; dev = dev->next) {
            if ((dev->descriptor.idVendor == vendor) && (dev->descriptor.idProduct == product)) {
                return dev;
            }
        }
    }

    return NULL;
}


static void sendData(struct usb_dev_handle *handle, const char* file) {
    
    char *data;
    int rv = 0;
    
    rv = usb_claim_interface(handle, 0);
    if (rv < 0) {
        printf("error claiming usb interface: %i\n", rv);
        exit(-1);
    }
 
    string line;
    ifstream myfile (file);
    if (myfile.is_open()) {
        while (! myfile.eof() ) {
            getline (myfile,line);
            
            if (line.length() == 0) {
                continue;
            }
            
            data = (char *) malloc(line.length()*sizeof(char));
            
            for (int i=0;i<line.length();i+=2) {
                string sub = line.substr(i, 2);
                char *end_ptr;
                long l = strtol(sub.c_str(), &end_ptr, 16);
                data[i/2] = l;
            }
            rv = usb_bulk_write(handle, 0x02, data, line.length()/2, 100);
            if (rv != line.length()/2) {
                printf("%i\n", rv);
            }

        }
        myfile.close();
    }

    else cout << "Unable to open file"; 
    
}

int main (int argc,char **argv)
{

    struct usb_device *dev;
    dev = findRelay(0x1a86,0x5512);

    if (dev == NULL) {
        fprintf(stderr, "USB device not found!\n");
        return 1;
    }

    usb_set_debug(3);
    
    
    usb_dev_handle *handle = usb_open(dev); 
    
    if (handle==NULL) {
        printf("error: no device handle\n");
        return 1;
    }


    set<int> active_relays;
    for (int i = 1; i<argc; i++) {
        int relay = atoi(argv[i]);
        if (relay < 1 || relay > 8) {
            cout << "error: only give valid relay numbers (1-8) as parameter" << endl;
            cout << "e.g. ./switch-relay 1 5 7" << endl;
            return 2;
        }
        active_relays.insert(atoi(argv[i]));
    }

    sendData(handle, "header.raw");
    for (int relay = 8; relay >=1; relay--) {
        if (active_relays.find(relay) != active_relays.end()) {
            sendData(handle, "on.raw");
        } else {
            sendData(handle, "off.raw");
        }
    }
    sendData(handle, "footer.raw");
    
    return 0;
}


This works perfectly well on my ubuntu 10.04 desktop pc, but not on the server?? 
I get the message: 'Segmentation fault' and nothing else
The server pc is a Pentium 2, 300Mhz 160MB Ram
The board is connected to a USB 2.0 card (Same problem with USB 1)

If I type lsusb, the board is found (ID), just the description is 'Unknown'. 

My question is: Does anybody know this board? 
Or: Where is the difference between USB on Ubuntu server and desktop? Do I have to install something on the server, which is installed on the desktop?

Thank you very much for your answers!

---

