# README
# Traceroute Program in Python

This Python program mimics the functionality of the traditional `traceroute` command-line tool. It sends ICMP Echo Request packets to a specified destination, increments the Time-to-Live (TTL) value for each packet, and observes the network path, printing out the IP addresses of each hop (router) along the way.

## Features

- **Trace network routes**: Sends ICMP Echo Request packets to a target host, displaying the IP address of each intermediate router.
- **Incremental TTL**: Uses TTL to incrementally discover each hop in the network path.
- **Timeout handling**: Displays a timeout message if a hop does not respond within a specified timeframe.
- **Command-line options**: Configurable maximum hops (`--max-hops`) and timeout for each packet response (`--timeout`).

## Requirements

- **Python 3**
- **Scapy library**: Install it using `pip install scapy`.

### Important Note
This program requires administrative privileges to send raw packets. Run the script with elevated permissions (e.g., `sudo` on Unix-like systems).

## Usage

The script is executed from the command line with the following syntax:

```bash
sudo python traceroute.py <destination> [options]

## Parameters
<destination>: The domain name or IP address of the target host to trace.
Options
-m or --max-hops: (Optional) Specify the maximum number of hops to trace. Defaults to 30 if not provided.
-t or --timeout: (Optional) Specify the timeout for each packet response in seconds. Defaults to 2 seconds if not provided.

## Sample Commands
sudo python traceroute.py example.com
sudo python traceroute.py google.com --max-hops 20 --timeout 1

## Sample Output
Traceroute to example.com (93.184.216.34), 30 hops max
1 192.168.1.1 RTT=1.234 ms
2 10.0.0.1 RTT=12.345 ms
3 172.16.0.1 RTT=24.567 ms
4 * Request timed out.
5 93.184.216.34 RTT=48.901 ms (Destination reached)