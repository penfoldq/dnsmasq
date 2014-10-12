#dnsmasq
========

Configuration files for the DNS and DHCP server for home LAN.

Running on a Raspberry Pi, with Raspbian Stable (Wheezy).

Wireless Router set to not provide DHCP service to the LAN but still run DHCP 
client on the WAN port. Router is configured with static LAN IP address of 
192.168.11.1/24.

The RPi is configured with the hostname `dnsmasq` and IP 192.168.11.2/24.

Install the "dnsmasq" package on the RPi and clone this repository onto the 
device. Either clone it directly into `/etc` or (preferably) clone it to some 
other location and link `dnsmasq.d` into `/etc`. `dnsmasq.conf` is 
deliberately left unchanged from the distribution package.

Inside `dnsmasq.d` is `penfoldq.net.conf` which contains the main 
configuration for all the options relevant to providing DNS and DHCP service 
for the home LAN. However, this file does not contain any of the DHCP lease 
information (`dhcp-hosts` stanzas) which are instead in the file 
`dhcp-hosts.conf`. 

This `dhcp-hosts.conf` file is expected to change regularly as new hosts are 
explicitly named. The configuration is set to provide an IP address from the 
dynamic pool for all unknown MAC addresses, but once a device should be named 
for easier identification, a line should be added to `dhcp-hosts.conf` and 
this update pushed to GitHub for backup.

It's optional but for the sake of easier debugging, 'localhost' should be 
added to `/etc/resolv.conf` (after '192.168.11.1') to provide reflection of 
the names issued by DHCP to the `dnsmasq` device itself.

  
