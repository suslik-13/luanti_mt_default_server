# SHELTER techage - Minetest/Luanti Server

## Description

This server contains default Luanti settings and default MineTest mods. It is intended to be used as a base for creating new servers.

## Server Launch

### Requirements
- Docker
- Docker Compose

### Launch Commands

To start the server use:

```bash
docker compose up
```

To start in background mode:

```bash
docker compose up -d
```

To stop the server:

```bash
docker compose down
```

### Fixing Permission Issues

If you encounter errors related to file configuration or log access permissions during startup, such as:

```
ERROR[Main]: Failed to open "/home/minetest/.minetest/debug.txt": Permission denied
ERROR[Main]: Could not read configuration from "/home/minetest/.minetest/minetest.conf"
```

Run the following command to fix access permissions:

```bash
sudo chmod -R 777 ./luanti_files
```

This command sets full access permissions (read/write/execute) to all files and directories inside `luanti_files`, allowing the Docker container to work freely with configuration, worlds, and mods.

## Project Structure

```
.
├── docker-compose.yml         # Docker Compose configuration
├── luanti_files/              # Server data (mounted in container)
│   ├── minetest.conf          # Main server config
│   ├── games/                 # Game mods and resources
│   │   └── minetest_game/     # Main game with mods
│   ├── worlds/                # Saved worlds
│   │   └── world/             # Server world
│   ├── mod_data/              # Mods data
└── README.md                  # This file
```

## Network Ports

The server uses the following ports:
- **30000/udp** — main game port
- **30000/tcp** — additional TCP port

Make sure these ports are open in your firewall if you want players to connect from outside.

## Configuration

The main configuration file is located at `./luanti_files/minetest.conf`. You can edit server settings by modifying this file.

After changing the configuration, restart the server:

```bash
docker compose restart
```

## Support

If you have problems or questions, join our Discord server: https://discord.gg/JUFdNDWAcu

---
