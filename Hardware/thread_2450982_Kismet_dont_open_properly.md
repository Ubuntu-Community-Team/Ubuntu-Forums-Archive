---
title: "Kismet dont open properly"
date: 2020-09-24
forum: Hardware
---

### Post by gtsapour on 2020-09-24
I am trying to work Kismet for educational reasons in Ubuntu 20.04. When  I start it I cannot see the wifi networks and i dont know if my network  card is the problem. i have a ath10k_pci. 

When i am typing 
[HTML]sudo kismet -c wlp2s0mon[/HTML]

[QUOTE][
Registering support for DLT_PPI packet header decoding
INFO: Registering support for DLT_RADIOTAP packet header decoding
INFO: Registering support for DLT_BTLE_LL_RADIO packet header decoding
INFO: Using default rates of 10/min, 1/sec for alert 'BADFIXLENIE'
INFO: PHY802.11 will not process Wi-Fi 'phy' and 'control' frames; these 
      typically are the most susceptible to corruption resulting in false 
      devices.  This can be re-enabled with dot11_process_phy=true
INFO: Allowing Kismet clients to view WEP keys
INFO: Keeping EAPOL packets in memory for easy download and WIDS 
      functionality; this can use more RAM.
INFO: Registered PHY handler 'IEEE802.11' as ID 0
INFO: Registered PHY handler 'RTL433' as ID 1
INFO: Registered PHY handler 'Z-Wave' as ID 2
INFO: Registered PHY handler 'Bluetooth' as ID 3
INFO: Registered PHY handler 'UAV' as ID 4
INFO: Registered PHY handler 'NrfMousejack' as ID 5
INFO: Registered PHY handler 'BTLE' as ID 6
INFO: Registered PHY handler 'RTLAMR' as ID 7
INFO: Indexing ADSB ICAO db
INFO: Completed indexing ADSB ICAO db, 325071 lines 6502 indexes
INFO: Registered PHY handler 'RTLADSB' as ID 8
INFO: Could not open system plugin directory (/usr/local/lib/kismet/), 
      skipping: No such file or directory
INFO: Did not find a user plugin directory (/root/.kismet//plugins/), 
      skipping: No such file or directory
INFO: GPS track will be logged to the Kismet logfile
INFO: Enabling channel hopping by default on sources which support channel 
      control.
INFO: Setting default channel hop rate to 5/sec
INFO: Enabling channel list splitting on sources which share the same list 
      of channels
INFO: Enabling channel list shuffling to optimize overlaps
INFO: Sources will be re-opened if they encounter an error
INFO: Saving datasources to the Kismet database log every 30 seconds.
INFO: Launching remote capture server on 127.0.0.1 3501
INFO: Data sources passed on the command line (via -c source), ignoring 
      source= definitions in the Kismet config file.
INFO: Probing interface 'wlp2s0mon' to find datasource type
INFO: Opened kismetdb log file './/Kismet-20200924-12-53-07-1.kismet'
INFO: Saving packets to the Kismet database log.
ALERT: rootuser Kismet is running as root; this is less secure.  If you 
       are running Kismet at boot via systemd, make sure to use `systemctl 
       edit kismet.service` to change the user.  For more information, see 
       the Kismet README for setting up Kismet with minimal privileges.
INFO: Starting Kismet web server...
INFO: (HTTPD) Started http server on port 2501
INFO: Found type 'linuxwifi' for 'wlp2s0mon'
INFO: wlp2s0mon interface 'wlp2s0mon' looks to use the ath10k_pci driver, 
      which is known to report large numbers of invalid packets. Kismet 
      will attempt to filter these but it is not possible to cleanly 
      filter all of them; you may see large quantities of spurious 
      networks.
INFO: wlp2s0mon interface 'wlp2s0mon' is already in monitor mode
INFO: Data source 'wlp2s0mon' launched successfully

/QUOTE]

Can anyone help me?

---

