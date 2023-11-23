-- Crear la tabla de Candidatos
CREATE TABLE Candidato (
    CandidatoID INT PRIMARY KEY,
    NombreCompleto VARCHAR(100),
    Edad INT,
    PartidoPolitico VARCHAR(50),
    CostoCampaña DECIMAL(10, 2),
    VotosObtenidos INT,
    PorcentajeVotos DECIMAL(5, 2)
);

-- Crear la tabla de Votos
CREATE TABLE Votos (
    VotoID INT PRIMARY KEY,
    CandidatoID INT,
    MedioComunicacion VARCHAR(50),
    FOREIGN KEY (CandidatoID) REFERENCES Candidato(CandidatoID)
);

-- Crear la tabla de Campana
CREATE TABLE Campana (
    MedioComunicacionID INT PRIMARY KEY,
    NombreMedio VARCHAR(50),
    CostoInfluencia DECIMAL(10, 2)
);

-- Formato para insertar
INSERT INTO Campana (MedioComunicacionID, NombreMedio, CostoInfluencia)
VALUES
    (1, 'Televisión', 1000),
    (2, 'Radio', 500),
    (3, 'Internet', 100);

INSERT INTO Votos (VotoID,CandidatoID, MedioComunicacion)
VALUES 
(1,1029, 'Televisión'),
(2,1029, 'Televisión'),
(3,1029, 'Internet'),
(4,1029, 'Radio');

-- Formato para insertar candidato
INSERT INTO Candidato (CandidatoID,NombreCompleto, Edad, PartidoPolitico, CostoCampaña, VotosObtenidos, PorcentajeVotos)
VALUES (1029,'Enrique Martínez', 49, 'Nuevos caminos', 11000800, 450, 45);


-- Formato para actualizar campaña
UPDATE Candidato SET CostoCampaña = CostoCampaña + (
    SELECT SUM(CostoInfluencia) AS CostoInfluencia
    FROM Votos
    INNER JOIN Campana ON Votos.MedioComunicacion = Campana.NombreMedio
    WHERE Votos.CandidatoID = @CandidatoID
    GROUP BY Votos.CandidatoID;
)
WHERE CandidatoID = @CandidatoID;
