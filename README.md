local thành«mod» = {}

thành«mod» = {
    [2753915549] = { Url = "https://raw.githubusercontent.com/flazhy/QuantumOnyx/main/BloxFruit.lua", Title = "BloxFruit" },
    [4442272183] = { Url = "https://raw.githubusercontent.com/flazhy/QuantumOnyx/main/BloxFruit.lua", Title = "BloxFruit" },
    [7449423635] = { Url = "https://raw.githubusercontent.com/flazhy/QuantumOnyx/main/BloxFruit.lua", Title = "BloxFruit" },
    [126884695634066] = { Url = "https://raw.githubusercontent.com/flazhy/QuantumOnyx/main/GAG.lua", Title = "Grow A Garden" },
}

function thành«mod»:GetScriptEntry(PlaceId: number)
    return self.Scripts[PlaceId]
end

function thành«mod»:LoadScript(entry: {Url: string, Title: string})
    if not entry then return end
    local ok, fn = pcall(function()
        return loadstring(game:HttpGet(entry.Url))
    end)
    if ok and fn then
        task.spawn(fn)
    end
end

function thành«mod»:LoadForPlace(PlaceId: number)
    local entry = self:GetScriptEntry(PlaceId)
    self:LoadScript(entry)
end

thành«mod»:LoadForPlace(game.PlaceId)

return thành«mod»
