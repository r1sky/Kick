# Kick
bukkit plugin
package me.Cpogo28.bukkit;

import java.util.logging.Logger;

import org.bukkit.ChatColor;
import org.bukkit.command.Command;
import org.bukkit.command.CommandSender;
import org.bukkit.entity.Player;
import org.bukkit.plugin.PluginDescriptionFile;
import org.bukkit.plugin.java.JavaPlugin;

public class kick extends JavaPlugin{
	public final Logger logger = Logger.getLogger("Minecraft");
	public static kick plugin;
	
	@Override
	public void onDisable() {
		PluginDescriptionFile pdfFile = this.getDescription();
		this.logger.info(pdfFile.getName() + " Has Been Disabled");
	}
	
	@Override
	public void onEnable() {
		PluginDescriptionFile pdfFile = this.getDescription();
		this.logger.info(pdfFile.getName() + " Version " + pdfFile.getVersion() + " Has Been Enabled");
	}
	@Override
	public boolean onCommand(CommandSender sender, Command cmd, String Label, String[] args) {
		Player player = (Player) sender;
		String name = player.getName();
		if(cmd.getName().equalsIgnoreCase("execute")){
			@SuppressWarnings("deprecation")
			Player target = sender.getServer().getPlayer(args[0]);
			// Make sure player is online.
			if (target == null) {
				sender.sendMessage(args[0] + "is not online");
				return true;
			}
			target.damage(20);
			target.sendMessage(ChatColor.DARK_RED + "You have been executed by " + name);
		}
		return false;
	}
}
