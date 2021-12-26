---init
local library = loadstring(game:HttpGet("https://raw.githubusercontent.com/GreenDeno/Venyx-UI-Library/main/source.lua"))()
local venyx = library.new("RIP#9999", 5013109572)
---Page 1
local page = venyx:addPage("Main", 5012544693)
---Section 1
local sectionautofarm = page:addSection("Auto Farm")
sectionautofarm:addToggle("Auto Click", false, function(t)
    _G.autoclick = t
end)
sectionautofarm:addToggle("Auto Sell", false, function(t)
    _G.autosell = t
end)
---Section 2
local sectiontp = page:addSection("Teleport")
sectiontp:addButton("Go to Sell", function()
    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = game:GetService("Workspace").sellAreaCircles.sellAreaCircle.circleInner.CFrame
end)
sectiontp:addButton("Go to Shop", function()
    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = game:GetService("Workspace").shopAreaCircles.shopAreaCircle.circleInner.CFrame
end)
sectiontp:addButton("Go to Skills", function()
    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = game:GetService("Workspace").skillAreaCircles.skillsAreaCircle.circleInner.CFrame
end)
---spawn function
spawn(function()
    while wait() do
        if _G.autoclick == true then
            game:GetService("Players").LocalPlayer.ninjaEvent:FireServer("swingKatana")
        end
    end
end)
spawn(function()
    while wait(3) do
        if _G.autosell == true then
            game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = game:GetService("Workspace").sellAreaCircles.sellAreaCircle.circleInner.CFrame
        end
    end
end)
---Page 2
local page2 = venyx:addPage("Misc", 5012544693)
local sectionsetting = page2:addSection("Settings")
sectionsetting:addKeybind("Toggle Keybind", Enum.KeyCode.RightControl, function()
    print("Activated Keybind")
    venyx:toggle()
end, function()
print("Changed Keybind")
end)
for theme, color in pairs(themes) do -- all in one theme changer, i know, im cool
colors:addColorPicker(theme, color, function(color3)
venyx:setTheme(theme, color3)
end)
end
---load
venyx:SelectPage(venyx.pages[1], true)
